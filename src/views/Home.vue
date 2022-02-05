<template>
  <div class="home">
    <transition name="toast">
        <Toast v-if="showToast" />
    </transition>
    <Todos @badValue="triggerToast" />
        <!-- <div v-if="display">Hi reina</div> -->
  </div>
</template>

<script>
import { ref } from 'vue'
import Toast from '../components/Toast'
import Todos from '../components/Todos'

export default {
  components: { Toast, Todos },
//   data(){
//       return{
//           display: false

//       }
//   },
  setup() {
    const showToast = ref(false)
    const display = ref(false)

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => showToast.value = false, 3000)
    }

    return { showToast, triggerToast, display }
  },
  methods:{
      displayMsg(){
          this.display = !this.display;
      }
  }


}
</script>

<style>
/* enterclasses */
.toast-enter-from{
    opacity: 0;
    transform: translateY(-60)
}
.toast-enter-to{
    opacity:1;
    transform: translateX(0)
}
.toast-enter-active{
    transition: all 3s ease;

}


/* this is the state at the beggining */
.fade-enter-from{
 opacity:0;
}

.fade-enter-to{
opacity:1;
}
/* how do we transit from one place to another */
.fade-enter-from-active{
transition: all 2s ease;
}

.fade-leave-from{
    opacity:1;

}
/* where we want to end up */
.fade-leave-to{
    opacity: 0;
}

.fade-leave-active{
transition: all 1s ease;
}
</style>