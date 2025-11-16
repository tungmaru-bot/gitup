<template>
  <header>
    <div class="logo">URLstn</div>
  </header>

  <div class="main-wrapper">
    <div class="card">
      <h2>Enter your link</h2>

      <input class="input-box" placeholder="Link Here" />

      <br><br>

      <button class="button-primary">shorten</button>

      <br><br>
      <input class="input-box" placeholder="the shortened link ưill appear here" readonly />

    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import axios from "axios";

const originalUrl = ref("");
const shortUrl = ref("");
const error = ref("");

async function shortenUrl() {
  error.value = "";
  shortUrl.value = "";

  try {
    const res = await axios.post("http://localhost:5000/api/url/shorten", {
      originalUrl: originalUrl.value
    });

    shortUrl.value = `http://localhost:5000/${res.data.code}`;
  } catch (err) {
    error.value = "invalid URL or wrong address !";
  }
}
</script>

<style>

</style>