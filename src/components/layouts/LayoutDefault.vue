<template>
  <div class="admin">
    <app-drawer ref="drawer" class="admin_drawer" @drawer:collapsed="mini = !mini" />
    <theme-settings ref="theme" />
    <app-toolbar
      class="admin_toolbar"
      extended
      @side-icon-click="handleDrawerVisiable"
      @theme-setting-click="handleThemeSetting"
    />
    <v-main class="grey lighten-3">
      <!-- Page Wrapper -->
      <div class="page_wrapper"><router-view /></div>
    </v-main>
    <!-- Go to top -->
    <app-fab />
  </div>
</template>

<script>
import AppDrawer from '@/components/AppDrawer'
import AppToolbar from '@/components/AppToolbar'
import AppFab from '@/components/AppFab'
import ThemeSettings from '@/components/ThemeSettings'

export default {
  name: 'LayoutDefault',
  components: {
    AppDrawer,
    AppToolbar,
    AppFab,
    ThemeSettings,
  },

  data() {
    return {
      mini: false,
      showDrawer: true,
    }
  },
  methods: {
    handleDrawerVisiable() {
      this.$refs.drawer.toggleDrawer()
    },
    handleThemeSetting() {
      this.$refs.theme.toggleThemeSetting()
    },
  },
}
</script>

<style lang="sass" scoped>
.page_wrapper
  min-height: calc(100vh - 112px - 48px)
  padding-top: 35px
  .container
    max-width: 1200px
</style>
