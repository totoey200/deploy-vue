<template>
  <div class="col-sm-4 col-sm-offset-4 mr-auto ml-auto">
    <h2>Log In</h2>
    <p>연합아이디어톤에 오신걸 환영합니다!</p>
    <div class="alert alert-danger" v-if="error">
      <p>{{ error }}</p>
    </div>
    <div class="form-group">
      <input
        type="text"
        class="form-control"
        placeholder="Enter your username"
        v-model="credentials.username"
        v-on:keyup.enter="submit()"
      >
    </div>
    <div class="form-group">
      <input
        type="password"
        class="form-control"
        placeholder="Enter your password"
        v-model="credentials.password"
        v-on:keyup.enter="submit()"
      >
    </div>
    <button class="btn btn-primary" @click="submit()">로그인</button>
  </div>
</template>
<script>
import auth from '../auth'
import axios from 'axios'

export default {
  name: 'Login',
  data () {
    return {
      credentials: {
        username: '',
        password: ''
      },
      error: ''
    }
  },
  methods: {
    submit () {
      var credentials = {
        username: this.credentials.username,
        password: this.credentials.password
      }
      console.log(credentials)
      auth.login(this, credentials, '/home')
    }
  },
  beforeCreate () {
    auth.checkAuth()
  }
}
</script>
