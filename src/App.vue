<template>
  <div class='fullview'>
    <Navbar :brand='brand' :pages='pages' :buttons='buttons' />
    <router-view :user = 'user' />
  </div>
</template>

<script>
import Navbar from '@/components/Navbar'

export default {
  components: {
    Navbar,
  },
  data() {
    return {
      user: null,
      brand: 'Forums',
      buttons: [{ "name":"Login", "link":"/login" }],
      pages: [{ "name":"Home", "link":"/" }, { "name":"Threads", "link":"/threads" }]
    }
  },
  created() {
    if(this.user !== null) {
      this.buttons = [{ "name":"My Profile", "link":"/me" }]
    }
  }
}
</script>

<style>
a {
  cursor: pointer;
}

.fullview {
  min-height: 100vh;
  width: 100%;
}

.page {
  margin: 16px 12px 10px 12px;
}

.flex {
  display: flex;
  flex-direction: column;
}

.row {
  flex-direction: row;
}

.center {
  justify-content: center;
  align-items: center;
}
</style>
