<template>
  <div class="login">
    <el-card>
      <h2>登录</h2>
      <el-form
          class="login-form"
      >
        <el-form-item prop="username">
          <el-input v-model="model.username" placeholder="用户名" ></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input
              placeholder="密码"
              type="password"
              v-model="model.password"
          ></el-input>
        </el-form-item>
        <el-row>
          <el-col class="register">
            还没有账号？请点击 <router-link class="to-link" :to="{path: '/register'}"><el-link type="primary" >注册</el-link></router-link>
          </el-col>
        </el-row>
        <el-form-item>
          <el-button
              class="login-button"
              type="primary"
              native-type="submit"
              @click="handleLogin"
              block
          >登录</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
import request from '../../utils/request'

export default {
  name: "login",
  data() {
    return {
      model: {
        username: "",
        password: ""
      },
    };
  },
  methods: {
    handleLogin() {
      this.$store.dispatch('user/login', this.model).then(() => {
        this.$router.push({ path: this.redirect || '/' })
      }).catch(() => {
      })
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.to-link {
  text-decoration:none;
}
.register {
  font-weight: 500;
  font-size: 14px;
}
.login {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

.login-button {
  width: 100%;
  margin-top: 40px;
}
.login-form {
  width: 390px;
}
.forgot-password {
  margin-top: 10px;
}
</style>
