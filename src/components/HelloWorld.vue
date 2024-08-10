<template>
  <h1>{{ msg }}</h1>
  <div class="cesium-container" ref="mapRef" />
</template>

<script lang="ts">
import { ref, defineComponent, onMounted } from "vue";
/**
 * You can also import Cesium Object like this
 *
 * import * as Cesium from 'cesium';
 * const viewer = new Cesium.Viewer('cesiumContainer');
 */
import { Viewer } from "cesium";
export default defineComponent({
  name: "HelloWorld",
  props: {
    msg: {
      type: String,
      required: true,
    },
  },
  setup: () => {
    const mapRef = ref<HTMLDivElement | null>(null);

    onMounted(() => {
      mapRef.value && new Viewer(mapRef.value);
    });
    return { mapRef };
  },
});
</script>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
.cesium-container {
  width: 500px;
  height: 250px;
  margin: 0 auto;
}
</style>
