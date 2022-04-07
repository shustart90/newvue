<template>
  <section class="slider-block">
    <div class="buttons-block slider-block__buttons-block">
      <div class="buttons-block__button buttons-block__button_l" @click="prevCard"></div>
      <div class="buttons-block__button buttons-block__button_r" @click="nextCard"></div>
    </div>
    <div class="slider slider-block__slider" :style="{left: this.offset + 'px'}">
      <div :id="'user-'+ card.id" v-for='(card, index) in $root.cardsList' class="card slider__card" :key="card.id">
        <img class="slider__photo" :src="imageAdress + (card.id - 1)" alt="" @click="$root.clickEffect" :class="{ 'card_focused': index === 0 }">
        <p class="slider__name" @click="$root.clickEffect" :class="{ 'focused-text': index === 0 }">{{card.name}}</p>
        <p class="slider__company" @click="$root.clickEffect" :class="{ 'focused-text': index === 0 }">{{card.company.name}}</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: ["cardsCount"],
  data () {
    return {
      imageAdress: "https://i.pravatar.cc/290?img=3",
      trueCounter: 1, // переменная-счетчик для контроля сдвига слайдера если она больше или меньше определенного значения слайдер перестает двигаться
      offset: 0,
    }
  },
  methods: {
    nextCard () { // следующая карточка с разработчиком
      if (this.trueCounter < this.cardsCount - 3) {
        this.offset -= 324
        this.trueCounter += 1
      }
    },
    prevCard () { // предидущая карточка с разработчиком
      if (this.trueCounter > 1) {
        this.offset += 324
        this.trueCounter -= 1
      }
    }
  }
}
</script>

<style>

</style>