<template>
  <div style="position: relative">
    Color : <input type="text" readonly v-model="color" />
    <button
      :style="{ background: color }"
      @click="showcolorpicker = showcolorpicker ? false : true"
    >
      &nbsp; chooseColor
    </button>

    <div v-show="showcolorpicker" style="position: absolute">
      <ColorPicker
        theme="light"
        :color="color"
        :sucker-hide="false"
        :sucker-canvas="suckerCanvas"
        :sucker-area="suckerArea"
        @changeColor="changeColor"
        @openSucker="openSucker"
      />
    </div>
</template>

<script>
import { ColorPicker } from 'vue-color-kit';
import 'vue-color-kit/dist/vue-color-kit.css';
import { ref } from 'vue';
export default {
  name: 'Colorpicker',
  components: {
    ColorPicker,
  },
  setup() {
    let color = ref('#FF007B');
    let suckerHide = ref(false);
    let suckerCanvas = null;
    let suckerArea = ref([]);
    let showcolorpicker = ref(true);
    function changeColor(_color) {
      //const { r, g, b, a } = _color.rgba;
      //color.value = `rgba(${r}, ${g}, ${b}, ${a})`;
      color.value = _color.hex;
    }
    function openSucker(isOpen) {
      if (isOpen) {
        // ... canvas be created
        // this.suckerCanvas = canvas
        // this.suckerArea = [x1, y1, x2, y2]
      } else {
        // this.suckerCanvas && this.suckerCanvas.remove
      }
    }
    return {
      color,
      suckerHide,
      suckerCanvas,
      suckerArea,
      changeColor,
      showcolorpicker,
      openSucker,
    };
  },
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
button{
  color:white;
}
</style>