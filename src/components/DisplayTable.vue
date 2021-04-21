<template>
  <table>
  <thead>
    <tr>
      <th>INDEX</th>
      <th>ID</th>
      <th>TITLE</th>
      <th>BODY</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(post, index) in postInfo" :key="post.id">
      <td>{{ index + 1 }}</td>
      <td>{{ post.id }}</td>
      <td>{{ post.title }}</td>
      <td>{{ post.body }}</td>
    </tr>
  </tbody>
</table>
</template>

<script>
import axios from 'axios';

export default {

  data(){
        return{
            postInfo: []
        };
    },

  created(){
      this.getpostInfo();
  },

  methods:{
    getpostInfo(){
        axios.get('https://jsonplaceholder.typicode.com/posts')
        .then(response => this.postInfo = response.data)
        .catch(error => this.postInfo = error.data);
    },      
  }  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table, th, td {
  border: 1px solid black;
}
</style>
