<template>
  <div class="container">
    <h1>Conversor de temperatura Celsius-Fahrenheit</h1>
    <input v-model="temperatura" type="number">
    <input @click="convertTemperatura" type="button">
    <h2>temperatura original</h2>
    <p>{{ temperatura }}</p>
    <h2>Temperatura convertida</h2>
    <p>{{ temperaturaConvertida }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      temperatura: 0,
      temperaturaConvertida: 0
    }
  },
  methods: {
    convertTemperatura() {
      this.$axios
        .get(`/convert/${this.temperatura}`)
        .then((res) => {
          this.temperaturaConvertida = res.value
        })
        .catch((err) => {
          console.error('Some error occurred')
        })
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
