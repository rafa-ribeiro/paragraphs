<template>
  <div>
    <p>{{ title }}</p>
  <div>
      <ul>
        <li v-for="(item, index) in items" :key="index">
          <nuxt-link :to='{name: "textSlug", params: {"textSlug": item.slug}}'>
            {{item.title}}
          </nuxt-link>          
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  layout: 'default',
  async asyncData(context) {
    return {
      'title': 'Paragraph',
      'items': await context.$content().sortBy('title').where({'published': true}).fetch(),
    };
  }
})

</script>
