<script setup>
import { ref, computed } from 'vue'

const noCount = ref(0)
const yesPressed = ref(false)
const showFinalMessage = ref(false)

const yesButtonSize = computed(() => noCount.value * 20 + 16)

const handleNoClick = () => {
  noCount.value++
}

const getNoButtonText = () => {
  const phrases = [
    'No',
    'Please 🥹',
    'Are you sure?',
    'Bitte schön 🥺',
    'What if I asked really nicely? 🥰',
    'With a chocolate cake on top',
    'What about a matcha frostie?',
    'PLEASE POOKIE',
    'Очень прошу тебя 🥺',
    'What if I take you out on 100 dates when you come back to Ingolstadt?',
    'But 😭',
    'I am going to die 😫',
    'Yep im dead 🫡',
    "ur talking to maksim's ghost now",
    'please babe',
    ':\u00A0(\u00A0(\u00A0(',
    'PRETTY PLEASE',
    'Ich bin tot',
    'No\u00A0:\u00A0(',
  ]

  return phrases[Math.min(noCount.value, phrases.length - 1)]
}
</script>

<template>
  <div class="container">
    <div class="card">
      <div v-if="yesPressed" class="success-screen">
        <div v-if="!showFinalMessage">
          <img
            src="https://media.tenor.com/2sK4kSCq240AAAAi/peach-goma-love-peach-goma.gif"
            alt=""
            style="width: 200px"
          />
          <div class="success-text">Yessss!!! I like you soooo much!! 🥰</div>
          <button class="continue-button" @click="showFinalMessage = true">A few words...</button>
        </div>
        <div v-else class="final-message">
          As you could've already guessed, I like you quite a lot. <br />
          You're the prettiest girl I've met. You're cute, gorgeous, sexy, and you have a great
          sence of humor, great hobbies, and you just have this amazing vibe that I can't get enough
          of – you are like a breath of fresh air. <br />
          Plus, you know, I don't have that many close friends in Ingolstadt, and you genuinely feel
          like you're my soulmate. Talking to you really lights up my day. I want to get to know you
          better and spend more time with you, take you out on dates, give you flowers, and kiss you
          once more. Hope this tiny gift of mine will brighten your St. Valentine's Day 💕💕
        </div>
      </div>
      <div v-else class="question-screen">
        <img
          class="main-image"
          src="https://media.tenor.com/XZfCF5WqSqMAAAAi/bear-flower.gif"
          style="width: 200px"
        />
        <h1 class="question">Anja, will you be my Valentine?</h1>
        <div class="buttons">
          <button
            class="yes-button"
            :style="{ fontSize: yesButtonSize + 'px' }"
            @click="yesPressed = true"
          >
            Yes
          </button>
          <button class="no-button" @click="handleNoClick">
            {{ noCount === 0 ? 'No' : getNoButtonText() }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: calc(100vh - 2rem * 2);
}

.card {
  background-color: white;
  padding: 3rem;
  border-radius: 0.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.success-screen {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.success-text {
  margin: 1rem 0;
  font-size: 2.25rem;
  font-weight: bold;
}

.question-screen {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.question {
  margin: 1rem 0;
  font-size: 2.25rem;
}

.buttons {
  display: flex;
  align-items: center;
  gap: 1rem;
}

button {
  padding: 0.5rem 1rem;
  font-weight: bold;
  color: white;
  border: none;
  border-radius: 0.375rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.yes-button {
  background-color: #22c55e;
}

.yes-button:hover {
  background-color: #16a34a;
}

.no-button {
  background-color: #ef4444;
}

.no-button:hover {
  background-color: #dc2626;
}

.continue-button {
  margin-top: 1.5rem;
  background-color: #ec4899;
  font-size: 1.2rem;
}

.continue-button:hover {
  background-color: #db2777;
}

.final-message {
  font-size: 1.4rem;
  text-align: left;
  max-height: 400px;
  overflow-y: scroll;
  padding-right: 1rem;
}

.final-message::-webkit-scrollbar {
  width: 4px;
}

.final-message::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 2px;
}

.final-message::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 2px;
}

.final-message::-webkit-scrollbar-thumb:hover {
  background: #555;
}
</style>
