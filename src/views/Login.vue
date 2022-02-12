<template>
  <div class="background-box">
    <div class="login-box">
      <div class="title">
        <h2>Requirements Engineering Tool</h2>
      </div>
      <el-form :model="loginForm" :rules="fieldRules" ref="loginForm">
        <!--line for username-->
        <el-form-item
          prop="username"
          style="width: 100%; margin: 20px 0 20px 0"
        >
          <el-input
            type="text"
            v-model="loginForm.username"
            auto-complete="off"
            placeholder="username"
          ></el-input>
        </el-form-item>
        <!--line for password-->
        <el-form-item
          prop="password"
          style="width: 100%; margin: 20px 0 20px 0"
        >
          <el-input
            type="password"
            v-model="loginForm.password"
            auto-complete="off"
            placeholder="password"
          ></el-input>
        </el-form-item>
        <!--line for two buttons-->
        <el-form-item style="width: 100%; margin: 20px 0 20px 0">
          <el-button
            type="primary"
            style="width: 30%; margin: 0 10% 0 10%"
            @click.native.prevent="reset"
            >Reset</el-button
          >
          <el-button
            type="primary"
            style="width: 30%; margin: 0 10% 0 10%"
            @click.native.prevent="login"
            >Login</el-button
          >
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data() {
    return {
      loginForm: {
        username: '',
        password: ''
      },
      fieldRules: {
        username: [
          { required: true, message: 'please enter username', trigger: 'blur' }
        ],
        password: [
          { required: true, message: 'please enter username', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    login() {
      this.$refs.loginForm.validate((valid) => {
        // valid means: all fields have no empty values
        if (valid) {
          // TODO  login logic was not implemented
          console.log('successed')
          this.$router.push('/')
        } else {
          console.log('failed')
        }
      })
    },
    reset() {
      this.$refs.loginForm.resetFields()
    }
  }
}
</script>

<style lang="scss" scoped>
.background-box {
  width: 100vw;
  height: 100vh;
  //background-color: #eee;
  background: url('~@/assets/images/festival.jpg') no-repeat center fixed;
  background-size: 100% 100%;
  // d
  overflow: hidden;
  display: flex;
  justify-content: center; // horizontal
  align-items: center; // vertical
  .login-box {
    //width: 30vw;
    min-width: 480px;
    min-height: 320px;
    border-radius: 20px;
    background-color: #fff;

    .title {
      margin: 40px;
      font-size: 20px;
      text-align: center;
    }

    .el-form {
      margin: 40px 80px 0 80px;
    }
  }
}
</style>
