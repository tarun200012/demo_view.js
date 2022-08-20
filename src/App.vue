<template>
  <div id="app">
      <h1>My todos app</h1>
      <ul>
        <li v-for="post of posts" :key="post.id">{{post.title}}</li>
      </ul>
  </div>
</template>

<script>

import axios from "axios";

export default {
  name: 'App',
  data() {
    return {
    posts: []
    }
    
  },
async created(){
  try{
    const res= await axios.get("http://localhost:3000/api/post");
    console.log(res);
    this.posts= res.data.data;
  }
  catch(e){
    console.error(e);
  }

}

}
</script>



<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #02070c;
  margin-top: 60px;
}
</style>
