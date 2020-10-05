<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" fixed temporary>
      <v-container>
    <v-list-item>
      <v-list-item-content>
        <v-list-item-title class="title grey--text text--darken-2">
          Navigation lists
        </v-list-item-title>
      </v-list-item-content>
    </v-list-item>
    <v-divider></v-divider>

     <v-list dense nav>
       <v-list-group v-for="fugu1 in fugus1"
       :key="fugu1.name"
       :prepend-icon="fugu1.icon"
       no-action
       :append-icon="fugu1.lists ? undefined : ''">
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>{{ fugu1.name }}</v-list-item-title>
          </v-list-item-content>
        </template>
        <v-list-item v-for="list in fugu1.lists" :key="list.name" :to="list.link">
          <v-list-item-content>
            <v-list-item-title> {{ list.name }}</v-list-item-title>
          </v-list-item-content>
     </v-list-item>
   </v-list-group>
   </v-list>
  </v-container>
    </v-navigation-drawer>

    <v-app-bar color="primary" dark app>
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>vuetify</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn text to="/poison">串カツ</v-btn>

        <v-menu offset-y>
          <template v-slot:activator="{on}">
          <v-btn v-on="on" text>フグ刺し
            <v-icon>mdi-menu-down</v-icon>
          </v-btn>

          </template>

          <v-list>
            <v-subheader>ヘルプ</v-subheader>
            <v-list-item v-for="fugu in fugus" :key="fugu" :to="fugu.link">
              <v-list-item-icon>
               <v-icon>{{ fugu.icon }}</v-icon>
             </v-list-item-icon>

             <v-list-item-content>
               <v-list-item-title>{{ fugu.name }}</v-list-item-title>
             </v-list-item-content>

            </v-list-item>
          </v-list>
        </v-menu>

      </v-toolbar-items>
    </v-app-bar>
    <v-main>
      <router-view></router-view>
    </v-main>
    <v-footer color="primary" dark app>
      Vuetify
    </v-footer>
  </v-app>
</template>

<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
<script>
export default{
  data(){
    return{
       drawer: null,
      fugus:[
        {name: '大阪',icon: 'mdi-vuetify',link:'/consulting-and-support'},
        {name: '神戸',icon: 'mdi-discord',link:'/discord-community'},
        {name: '山口',icon: 'mdi-bug',link:'/report-a-bug'},
        {name: '名古屋',icon: 'mdi-github',link:'/guthub-issue-board'},
        {name: '北海道',icon: 'mdi-stack-overflow',link:'/stack-overview'}
      ],
      fugus1:[
        {name: '大阪',icon: 'mdi-vuetify',lists: [{name: 'なんでやねん！',link: '/quick-start'},{name: 'アカン！',link: '/pre-made-layouts'}]},
        {name: '神戸',icon: 'mdi-discord' },
        {name: '山口',icon: 'mdi-bug',lists: [{name:'萩の月',link: '/hage'},{name: '秋吉台',link: '/karu'},{name: 'フグ',link: '/debu'}]},
        {name: '名古屋',icon: 'mdi-github'},
        {name: '北海道',icon: 'mdi-stack-overflow',lists: [{name: '蟹',link: '/kurabu'},{name: 'ウニ',link: '/kusami' }]}
      ]
    }
  }
}

</script>
