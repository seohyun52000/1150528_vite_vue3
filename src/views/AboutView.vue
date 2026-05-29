<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p class="name">{{ name }}</p>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
  .name {
    font-family: 'Noto Serif TC', serif;
  }
}
</style>
<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue'

const name = ref('')
onMounted(() => {
  console.log(import.meta.env.VITE_TEXT)
  const api = import.meta.env.VITE_PATH
  axios.get(api).then((res) => {
    if (res.status == 200) {
      name.value = res.data.results[0].name.first
    }
  })
})
</script>
