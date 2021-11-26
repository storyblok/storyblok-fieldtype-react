<template>
  <div>
    React in vue
    <div class="uk-form-row">
      <label>React field:</label>
      <my-react-component :title="model.title" @update="update" />
    </div>
  </div>
</template>

<script>
import MyReactComponent from './MyReactComponent'

export default {
  mixins: [window.Storyblok.plugin],
  components: { 'my-react-component': MyReactComponent },
  methods: {
    initWith() {
      return {
        // needs to be equal to your storyblok plugin name
        plugin: 'colorpickr1',
        title: '123'
      }
    },
    pluginCreated() {
      // eslint-disable-next-line
      console.log('View source and customize: https://github.com/storyblok/storyblok-fieldtype')
    },
    update(v) {
      console.log(v)
    }
  },
  watch: {
    'model': {
      handler: function (value) {
        this.$emit('changed-model', value);
      },
      deep: true
    }
  }
}
</script>
