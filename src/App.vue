<template lang="html">
  <div id="app">
    <img src="./assets/logo.png">

    <p v-show='showValue'>{{value}}</p>
    <p v-if='showValue'>{{value}}</p>
    <p v-else-if='false'>{{'algo más'}}</p>
    <p v-else>{{'lo ultimo'}}</p>
    <h1>{{ msg }}</h1>
    <ul>
      <li v-for = 'i in items'>{{i}}</li>
    </ul>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <h1>{{ msg }}</h1>
    <p>{{ 'hola' + 'hola2' }}</p>
    <p>{{ persona.name }}</p>
    <p>{{ persona.name.toUpperCase() }}</p>
    <p>{{ JSON.stringify(persona) }}</p>
    <p>{{ true ? 'true' : 'false' }}</p>
    <input type="text" v-model='name' />
    <p>{{name}}</p>
    <a v-bind:href="url">{{url}}</a>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>

    <input v-model='name' />
    <input v-model='lastName' />
    <p>{{fullName}}</p>
    <button v-on:click='format' type="button">Click Me!</button>
    <p>{{formattedName}}</p>


    <div class = 'container'>
      <input type="text" placeholder="Busca canciones" v-model='searchQuery'>
      <a href="#" class="button.is-info is-large" v-on:click='search'>Buscar</a>
      <a href="#" class="button is-info is-large">&times;</a>
      <p><small>{{searchMessage}}</small></p>

    </div>
    <div class = 'container'>
      <div class="column" v-for="item in tracks">{{item.name}} - {{item.artist}}</div>
    </div> 

    

  </div>
</template>

<script>

const tracks = [
  { name: 'muchacha', artist: 'Luis Alberto Spinetta' },
  { name: 'Hoy aca en el baile', artist: 'El Pepo' },
  { name: 'Iwas made for loving you', artist: 'kiss' },
];
export default {
  name: 'app',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      showValue: true,
      url: 'https://platzi.com',
      value: 'Algo',
      items: [1, 2, 3, 4, 5],
      name: '',
      lastName: '',
      persona: {
        name: 'Eduardo',
      },
      formattedName: '',
      searchQuery: '',
      tracks: [],
    };
  },
  methods: {
    search() {
      this.tracks = tracks;
    },
    format() {
      this.formattedName = this.name.split(' ').join('-').toUpperCase();
    },
  },
  computed: {
    searchMessage() {
      return `Encontramos: ${this.tracks.length}`;
    },
    fullName() {
      return `${this.name} ${this.lastName}`;
    },
  },
  watch: {
    name(newVal, oldVal) {
      console.log(newVal, oldVal);
    },
  },
};
</script>

<style lang='stylus'>
@import "./css/main.styl"
</style>
