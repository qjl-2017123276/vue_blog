<template>
  <div style="height: 100%;">
    <el-container style="height: 100%;">
      <el-header style="height: 60px; padding: 0;">
        <!--  -->

        <el-menu
          style="height: 100%;"
          class="el-menu"
          mode="horizontal"
          background-color="#333"
          text-color="#fff"
          active-text-color="#ffd04b"
        >
          <el-menu-item
            index="1"
            @click="getUser"
          >用户中心</el-menu-item>
          <el-submenu index="2">
            <template slot="title">我的工作台</template>
            <el-menu-item index="2-1">选项1</el-menu-item>
            <el-menu-item index="2-2">选项2</el-menu-item>
            <el-submenu index="2-4">
              <template slot="title">选项4</template>
              <el-menu-item index="2-4-1">选项1</el-menu-item>
            </el-submenu>
          </el-submenu>
          <el-menu-item index="3">消息中心</el-menu-item>
          <el-menu-item class="logout">
            <el-button>退了</el-button>
          </el-menu-item>
        </el-menu>
        <!--  -->
      </el-header>
      <el-container>
        <el-aside style="width: 240px; background-color: #545c64; overflow: hidden;">
          <!--  -->
          <el-menu
            style="width: 100%;"
            default-active="2"
            @open="handleOpen"
            @close="handleClose"
            background-color="#545c64"
            text-color="#fff"
            active-text-color="#ffd04b"
          >
            <!-- 文章管理 -->
            <el-submenu index="1">
              <template slot="title">
                <i class="el-icon-tickets"></i>
                <span>文章管理</span>
              </template>
              <el-menu-item-group>
                <el-menu-item
                  index="1-1"
                  @click="allArticle"
                >所有文章</el-menu-item>
                <el-menu-item
                  index="1-2"
                  @click="selectArticle"
                >查询文章</el-menu-item>
                <el-menu-item
                  index="1-3"
                  @click="addArticle"
                >添加文章</el-menu-item>
              </el-menu-item-group>
            </el-submenu>
            <!-- 文章分类管理 -->
            <el-submenu index="2">
              <template slot="title">
                <i class="el-icon-s-cooperation"></i>
                <span>分类管理</span>
              </template>
              <el-menu-item-group>
                <el-menu-item
                  index="2-1"
                  @click="allClassify"
                >所有分类</el-menu-item>
                <el-menu-item
                  index="2-2"
                  @click="addClassify"
                >添加分类</el-menu-item>
              </el-menu-item-group>
            </el-submenu>
            <el-submenu index="3">
              <template slot="title">
                <i class="el-icon-bell"></i>
                <span>评论管理</span>
              </template>
              <el-menu-item-group>
                <el-menu-item
                  index="3-1"
                  @click="allComment"
                >所有评论</el-menu-item>
                <!--  <el-menu-item
                  index="3-2"
                  @click="addClassify"
                >添加分类</el-menu-item> -->
              </el-menu-item-group>
            </el-submenu>
          </el-menu>
          <!--  -->
        </el-aside>
        <el-main style="min-width: 600px;">
          <router-view v-if="isRouterShow"></router-view>
        </el-main>
      </el-container>
    </el-container>
  </div>

</template>

<script>

export default {
  name: 'Main',
  data () {
    return {
      msg: 'Welcome to Main',
      isRouterShow: true
    }
  },
  methods: {
    handleOpen (key, keyPath) {
      console.log(key, keyPath)
    },
    handleClose (key, keyPath) {
      console.log(key, keyPath)
    },
    getUser: function () {
      this.$router.push({ path: '/main/user' })
    },
    allArticle: function () {
      this.$router.push({ path: '/main/article' })
    },
    selectArticle: function () {
      this.$router.push({ path: '/main/article/select' })
    },
    addArticle: function () {
      this.$router.push({ path: '/main/article/add' })
    },
    allClassify: function () {
      this.$router.push({ path: '/main/classify' })
    },
    addClassify: function () {
      this.$router.push({ path: '/main/classify/add' })
    },
    allComment: function () {
      this.$router.push({ path: '/main/comment' })
    }
  }
}

</script>
<style lang="less" scoped>
.logout {
  position: fixed;
  right: 20px;
  border: 0;
  padding: 0;
  height: 40px;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  //  text-align: center;
}
</style>
