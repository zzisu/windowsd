<template>
  <v-app>
    <v-system-bar app window style="-webkit-app-region: drag">
      <v-avatar size="32" class="mr-2" tile>
        <img src="@/../public/favicon.ico">
      </v-avatar>
      <v-spacer/>
      Windowsd
      <v-spacer/>
      <v-btn text @click="minimize" style="-webkit-app-region: no-drag">
        <v-icon class="no-margin">mdi-minus</v-icon>
      </v-btn>
      <v-btn text @click="maximize" style="-webkit-app-region: no-drag">
        <v-icon class="no-margin">mdi-plus</v-icon>
      </v-btn>
      <v-btn text @click="close" style="-webkit-app-region: no-drag" color="error">
        <v-icon class="no-margin">mdi-close</v-icon>
      </v-btn>
    </v-system-bar>
    <v-app-bar app>
      <v-app-bar-nav-icon @click="nav = !nav"/>
    </v-app-bar>
    <v-navigation-drawer v-model="nav" app>
      <v-list-item>
        <v-list-item-avatar>
          <v-icon>mdi-incognito</v-icon>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title>
            Guest
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-divider/>
      <v-list>
        <v-list-item to="/">
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item to="/settings">
          <v-list-item-action>
            <v-icon>mdi-settings</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Settings</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item @click="exit">
          <v-list-item-action>
            <v-icon>mdi-exit-to-app</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Exit</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-content>
      <v-container class="fill-height">
        <keep-alive>
          <router-view></router-view>
        </keep-alive>
      </v-container>
    </v-content>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue'
import Component from 'vue-class-component'
import { uiMinimize, uiMaximuze, uiClose, uiExit } from '@/frontend/ui'

@Component
export default class App extends Vue {
  nav = false
  minimize () {
    uiMinimize()
  }

  maximize () {
    uiMaximuze()
  }

  close () {
    uiClose()
  }

  exit () {
    uiExit()
  }
}
</script>

<style lang="scss" scoped>
.no-margin {
  margin: 0 !important;
}
</style>
