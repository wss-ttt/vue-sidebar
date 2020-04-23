<template>
  <div class="wrapper">
    <div class="sidebar">
      <el-scrollbar wrap-class="el-scrollbar-wrapper">
        <el-menu
          background-color="#304156"
          text-color="#fff"
          active-text-color="#409EFF"
          default-active="photo"
          :collapse="isCollapse"
          :collapse-transition="false"
        >
          <el-menu-item index="home">
            <i class="el-icon-document"></i>
            <span slot="title">首页</span>
          </el-menu-item>
          <el-menu-item index="photo">
            <i class="el-icon-document"></i>
            <span slot="title">相册</span>
          </el-menu-item>
          <el-menu-item index="blog">
            <i class="el-icon-document"></i>
            <span slot="title">博客</span>
          </el-menu-item>
          <el-menu-item index="news">
            <i class="el-icon-document"></i>
            <span slot="title">新闻</span>
          </el-menu-item>
          <el-menu-item index="nba">
            <i class="el-icon-document"></i>
            <span slot="title">NBA</span>
          </el-menu-item>
        </el-menu>
      </el-scrollbar>
    </div>
    <div class="container">
      <el-button @click="toggleSidebar">展开/折叠</el-button>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  props: {},
  data() {
    return {
      isCollapse: false
    }
  },
  watch: {},
  computed: {},
  methods: {
    toggleSidebar() {
      this.isCollapse = !this.isCollapse
      let wrapper = document.querySelector('.wrapper')
      wrapper.classList.toggle('hideSidebar')
    }
  },
  created() {},
  mounted() {}
}
</script>
<style scoped lang="scss">
/*去掉动画效果*/
.wrapper {
  height: 100%;
  .sidebar {
    // transition: width 0.28s;
    position: fixed;
    top: 0;
    left: 0;
    width: 210px;
    bottom: 0;
    height: 100%;
    background-color: #304156;
    overflow: hidden;
    // 滚动条样式的设置--开始
    .el-scrollbar {
      height: 100%;
    }
    // 滚动条样式的设置--结束
    .el-menu {
      border: none;
      height: 100%;
      /*原始的el-menu中的样式是width:64px*/
      /*现在我们是把width:64px添加了外城.sidebar的身上了*/
      width: 100% !important;
    }
  }
  .container {
    // transition: margin-left 0.28s;
    min-height: 100%;
    background-color: #ccc;
    margin-left: 210px;
  }
  &.hideSidebar {
    /*折叠的时候的width*/
    .sidebar {
      width: 64px;
    }
    .container {
      margin-left: 64px;
    }
  }
}
</style>
<style>
/* 该样式不能放在scoped中 */
.el-scrollbar-wrapper {
  overflow-x: hidden;
}
</style>