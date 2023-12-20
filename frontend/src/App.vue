<script setup lang="ts">
import { ref, onMounted, reactive } from 'vue'

const store = reactive({
  generations: <Array<string>>[]
})

function generateFilenames(n: number): string[] {
    let filenames: string[] = [];
    for (let i = 0; i < n; i++) {
        filenames.push(`output_${i}.png`);
    }
    return filenames;
}

store.generations = generateFilenames(30);


</script>

<template>
  <div class="common-layout">

    <el-container>

      <el-header class="header">
          <span>SERIOUS DANCERS ONLY</span>
      </el-header>

      <el-main class="gallery">
        <div class="centered-container">
          <audio controls>
            <source src="https://github.com/patch-star/sdo/raw/main/frontend/public/sdo.mp3" type="audio/mpeg">
          </audio>
        </div>
        <br/>
        <br/>
        <el-row>
          <el-col
            v-for="(generation, _) in store.generations"
            :key="generation"
            :span="24"
          >
            <el-card :body-style="{ padding: '0px' }">
              <img
                :src="generation"
                class="image"
              />
            </el-card>
          </el-col>
        </el-row>
      </el-main>

      <el-header class="footer">
        <span>
          <a href="mailto:jaclyn.ting@gmail.com">apply</a>
        </span>
      </el-header>
    </el-container>
  
  </div>
</template>

<style>

body {
  font-family: 'Martian Mono', monospace;
  font-weight: 900;
  background-color: #ffb6c1;
}

.header {
  text-align: center;
  /* font-size: 100px; */
  color: #c5c500;
  width: 100%; /* Set the width of the container */
  height: 100%; /* Set the height of the container */
  display: flex; /* Use Flexbox for alignment */
  justify-content: center; /* Center content horizontally */
  align-items: center; /* Center content vertically */
  font-size: 10vw; /* Set font size relative to viewport width */
}

.gallery {
  position: relative;
  min-height: 300px;
}

.footer a {
  color: #ca4353;
}

.time {
  font-size: 12px;
  color: #999;
}

.bottom {
  margin-top: 0px;
}

.button {
  padding: 0;
  min-height: auto;
}

.image {
  width: 100%;
  display: block;
}

.centered-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
}
</style>

