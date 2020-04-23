<template>
  <div id="app">
    <PostForm/>
    <strong>Posts count: {{postsCount}}</strong>
    <div class="post" v-for="post in validPost" :key="post.id">
      <h4 class="post__title">{{post.title}}</h4>
      <p class="post__body">{{post.body}}</p>
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
import PostForm from './components/PostForm'

export default {
  name: 'App',
  // computed: {
  //   getAllPosts() {
  //     return this.$store.getters.allPosts
  //   }
  // },
  components: { PostForm },
  computed: mapGetters(['validPost', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  async mounted() {
    // this.$store.dispatch('fetchPosts')
    this.fetchPosts(4)
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.post {
  margin-bottom: 40px;
}

.post__title {
  padding: 0;
  margin-bottom: 5px;
}

.post__title:first-letter {
  text-transform: uppercase;
}

.post__body {
  margin: 0;
}

</style>
