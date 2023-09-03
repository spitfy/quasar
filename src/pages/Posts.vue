<template>
  <q-page class="flex flex-center">
      <q-list bordered separator>
          <h2 style="margin-top: 50px">POSTS</h2>
          <q-item clickable v-ripple v-for="post in posts" :key="post.id">
              <q-item-section>
                  <q-item-label>{{ post.title }}</q-item-label>
                  <q-item-label caption>{{ post.body }}</q-item-label>
              </q-item-section>
          </q-item>
      </q-list>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'IndexPage',
    data() {
        return {
            posts: [],
        }
    },
    created() {
        this.$axios.get('https://jsonplaceholder.typicode.com/posts')
            .then(response => {
                this.posts = response.data
            })
    }
})
</script>
