<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"/>

        <q-avatar>
          <q-img  src="~assets/animalex.jpg"/>
        </q-avatar>
        <q-toolbar-title>
        TIENDA DE MASCOTAS
        </q-toolbar-title>

        <q-btn flat round dense icon="group_add" />
      </q-toolbar>


    </q-header>



    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :breakpoint="500"
      bordered
      class="bg-grey-3"
    >
      <q-item-label class="text-dark" header style="font-weight: bold" >TIENDA DE MASCOTAS</q-item-label>


        <q-list>
          <template v-for="(menuItem, index) in menuList" :key="index">
            <q-item clickable :active="menuItem.label === 'Outbox'" v-ripple>
              <q-item-section avatar>
                <q-icon :name="menuItem.icon" />
              </q-item-section>
              <q-item-section>
                <q-item-label>{{menuItem.title}}</q-item-label>
                <q-item-label caption lines="2">{{menuItem.descripcion}}</q-item-label>
              </q-item-section>
            </q-item>
            <q-separator  />
          </template>

        </q-list>


    </q-drawer>
<!--    <q-drawer-->
<!--      v-model="leftDrawerOpen"-->
<!--      show-if-above-->
<!--      class="bg-grey-2"-->
<!--      bordered-->
<!--    >-->
<!--      <q-list>-->
<!--        <q-item-label class="text-dark" header style="font-weight: bold"-->
<!--        >-->
<!--        ANIMALEX-->
<!--        </q-item-label>-->

<!--        <EssentialLink-->
<!--          v-for="link in essentialLinks"-->
<!--          :key="link.title"-->
<!--          v-bind="link"-->
<!--        />-->
<!--      </q-list>-->
<!--    </q-drawer>-->

    <q-page-container>
      <transition
        enter-active-class="animated slideInRight"
        leave-active-class="animated fadeOut"
        mode="out-in"
      >
        <router-view/>
      </transition>
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'


const menuList = [
  {
    title: 'Aves',
    descripcion: 'Accesorios,aves de diferentes tipos, comida y mucho m??s...',
    icon: 'account_tree',
    // link: 'https://quasar.dev'
  },
  {
    title: 'Peces',
    descripcion: 'Accesorios,peces,peceras,comidas y mucho m??s....',
    icon: 'account_tree',
    // link: 'https://github.com/quasarframework'
  },
  {
    title: 'Perros',
    descripcion: 'Accesorios,comidas,juguetes y mucho m??s...',
    icon: 'account_tree',
    // link: 'https://chat.quasar.dev'
  },
  {
    title: 'Roedores',
    descripcion: 'Accesorios,animales,comidas, y mucho m??s...',
    icon: 'account_tree',
    link: 'https://forum.quasar.dev'
  },
]
export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      menuList:menuList,
      // essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
