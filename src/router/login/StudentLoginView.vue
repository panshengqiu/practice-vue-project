<template>
  <div id="login_view" style="display: flex; flex-direction: column; height: 100vh;">
    <a-layout-header :style="headerStyle">
      <!-- Add a router-link button that toggles between student and enterprise login -->
      <router-link :to="currentView === 'studentLogin' ? '/enterpriseLogin' : '/studentLogin'" class="login-toggle" >
        {{ currentView === 'studentLogin' ? '企业入口' : '学生登入入口' }}
      </router-link>
      <img src="../../assets/OIG2.jpg" alt="not found picture" style="height: 64px; width: auto; align-self: flex-start;position: absolute; right: 0; border-radius: 50%">
    </a-layout-header>
    <div style="flex: 1; display: flex; align-items: center; justify-content: center; height: 600px">
      <a-layout-content :style="contentStyle" id="content">
        <login-form :style="{ marginBottom:'150px',marginRight:'600px',position: 'relative', zIndex: 1}"></login-form>
        <video class="background-video" autoplay loop muted>
          <source src="/登录背景.mp4" type="video/mp4">
        </video>
      </a-layout-content>
    </div>
    <a-layout-footer :style="footerStyle">
      实习徒团队倾情打造，有问题请联系管理员
      <br>
      <span>

      </span>
    </a-layout-footer>
  </div>
</template>

<script lang="ts" setup>

import { computed } from 'vue';
import { useRoute } from 'vue-router';
import type { CSSProperties } from 'vue';
import LoginForm from "../../components/login/LoginForm.vue";

const route = useRoute();
// 使用可选链来避免undefined的问题，并提供一个默认值
const currentView = computed(() => route.name ?? 'studentLogin');


const headerStyle: CSSProperties = {
  display: 'flex',
  alignItems: 'center',
  textAlign: 'center',
  height: '32px',
  paddingInline: '50px',
  lineHeight: '64px',
  backgroundColor: '#ffffff',
  position: 'relative', zIndex: 1 };

const contentStyle: CSSProperties = {
  textAlign: 'center',
  display: 'flex',
  alignItems: 'center',
  justifyContent: 'center',
  backgroundSize: 'cover',
  opacity: 0.9,
};

const footerStyle: CSSProperties = {
  textAlign: 'center',
  color: '#0c0202',
  height: '30px',
  lineHeight: '30px',
  backgroundColor: '#ffffff',
  position: 'relative', zIndex: 1
};

</script>

<style scoped>
#content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
  width: 100%;
  //background-image: url("../../../public/实习徒注册背景.gif");
  background-size: cover;
  opacity: 0.9;
}

.login-form {
  width: 100%;
  padding: 0;
  box-sizing: border-box;
}

.login-toggle {
  position: absolute;
  left: 20px;
  color: #fff;
  background-color: #22ff00;
  border: none;
  font-size: 16px;
  border-radius: 4px;
  text-decoration: none;
  transition: background-color 0.3s;
  z-index: 0;
}

.login-toggle:hover {
  background-color: #40a9ff;
}

.background-video {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover; /* 确保视频填充整个容器并保持宽高比例 */
  z-index: 0; /* 确保视频位于布局内容之后 */
}
</style>
