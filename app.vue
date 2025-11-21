<template>


  <div :class="isDark ? 'bg-neutral-100 text-black' : 'bg-neutral-950 text-neutral-100' "  class="min-h-screen flex flex-col items-center justify-start py-10 px-4">
    
    <!-- Bouton en haut à droite -->
    <button
      @click="toggleTheme"
      class="fixed top-4 right-4 px-4 py-2 rounded-full shadow-md font-semibold
             transition-all duration-300
             bg-white text-black dark:bg-black dark:text-white"
    >
      {{ isDark ? '🌙' : '☀️' }}
    </button>
    <!-- Logo -->
    <img src="@/assets/images/pdp.png" alt="Logo" class="w-48 h-48 rounded-full mb-6"/>

     <!-- Intro -->
    <h1  class="text-4xl font-bold text-center mb-3">
      <transition name="fade" mode="out-in">
        <span :key="isFrench">
          <span v-if="isFrench">Bonjour, moi c'est</span>
          <span v-else>Hello, I'm</span>
          <span class="text-emerald-600"> Lyes</span> ✨
        </span>
      </transition>
    </h1>

    <transition name="fade" mode="out-in">
      <p class="text-center  max-w-xl mb-8 text-lg" :key="isFrench">
        <span v-if="isFrench">
          Data Scientist & Engineer, obsédé par l’exploitation intelligente de la data et de l’IA pour concevoir des projets end-to-end qui résolvent des problématiques complexes avec efficacité et impact.        
        </span>
        <span v-else>
          Data Scientist & Engineer, obsessed with the intelligent exploitation of data and AI to design end-to-end projects that solve complex problems with efficiency and impact.
        </span>
      </p>
    </transition>

    <!-- Contact Links -->
    <div  class="flex flex-col gap-5 w-full max-w-xs mb-8">
      
      <a
        href="https://github.com/sheikhops"
        target="_blank"
        :class="isDark ? 'text-neutral-950 bg-gray-200 hover:bg-gray-400' : 'text-neutral-100 bg-gray-700  hover:bg-gray-400' "
        class="flex items-center justify-center gap-3 px-8 py-4 rounded-xl transition text-lg"
      >
        <img src="@/assets/images/github.png" alt="GitHub" class="w-8 h-8"/>
        <span class="text-center flex-1 font-semibold">GitHub</span>
      </a>

      <a
        href="https://www.linkedin.com/in/lyes-a-a22009388/"
        target="_blank"
        :class="isDark ? 'text-neutral-950 bg-gray-200 hover:bg-gray-400' : 'text-neutral-100 bg-gray-700  hover:bg-gray-400' "
        class="flex items-center justify-center gap-3 px-8 py-4 rounded-xl  transition text-lg"
      >
        <img src="@/assets/images/linkedin.png" alt="LinkedIn" class="w-8 h-8"/>
        <span class="text-center flex-1 font-semibold">LinkedIn</span>
      </a>

      <a
        href="https://www.kaggle.com/sheikhops19"
        target="_blank"
        :class="isDark ? 'text-neutral-950 bg-gray-200 hover:bg-gray-400' : 'text-neutral-100 bg-gray-700  hover:bg-gray-400' "

        class="flex items-center justify-center gap-3 px-8 py-4 rounded-xl transition text-lg"
      >
        <img src="@/assets/images/kaggle.svg" alt="Kaggle" class="w-8 h-8"/>
        <span class="text-center flex-1 font-semibold">Kaggle</span>
      </a>

      <a
        href="https://medium.com/@lyes.abdesselam"
        target="_blank"
        :class="isDark ? 'text-neutral-950 bg-gray-200 hover:bg-gray-400' : 'text-neutral-100 bg-gray-700  hover:bg-gray-400' "
        class="flex items-center justify-center gap-3 px-8 py-4 rounded-xl transition text-lg"
      >
        <img src="@/assets/images/medium.svg" alt="Blog" class="w-8 h-8"/>
        <span class="text-center flex-1 font-semibold">Blog</span>
      </a>

    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount,watchEffect } from "vue";

const isDark = ref(false)

const toggleTheme = () => {
  isDark.value = !isDark.value
}
const isFrench = ref(true);
let interval: number;

onMounted(() => {
  interval = setInterval(() => {
    isFrench.value = !isFrench.value;
  }, 10000); // change toutes les 5s
});

onBeforeUnmount(() => {
  clearInterval(interval);
});
// Ajoute / retire la classe dark sur <html>
watchEffect(() => {
  if (isDark.value) {
    document.documentElement.classList.add('dark')
  } else {
    document.documentElement.classList.remove('dark')
  }
})
</script>


<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.8s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
