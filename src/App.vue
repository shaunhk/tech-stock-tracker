<template lang="html">
  <div id="app">
    <p id="list" v-for="companyProfile in this.companyProfiles"><img id= "logo" :src="companyProfile.image">Company name: {{companyProfile.companyName}} Stock-price: {{companyProfile.price}}</p>
  </div>
</template>

<script>

export default {
  name: 'app',
  components: {

  },
  data(){
    return {
      companyProfiles: null,
      companySymbols: ['MSFT', 'APPL']
    }
  },
  mounted() {
    this.getCompanyProfile
  },
  methods: {
    getCompanyProfile(){
      const promises = companySymbols.map(symbol => {
    return fetch(`https://financialmodelingprep.com/api/v3/company/profile/${symbol}`)
    .then(response => response.json())
  })

  Promise.all(promises)
  .then(data => this.companyProfiles = data.map(company => {company.profile}))
  }
}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#logo {
  width: 20px;
  height: 20px;
}

#list {
  text-align: left;
}

</style>
