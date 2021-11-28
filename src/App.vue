<template>
  <button type="button" @click="onGetNoteClicked">Get Note</button>
  <p>Your note is: {{ note }}</p>
</template>

<script>
import { ref } from 'vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
  },
  setup() {
    const note = ref('')
    
    const onGetNoteClicked = () => {
      axios.get('http://localhost:8000/api/notes/').then((response) => {
	note.value = response.data[0].content
      })
    }

    return { note, onGetNoteClicked }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
