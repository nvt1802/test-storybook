<template>
  <button type="button" :class="classes" @click="onClick" :style="style">
    {{ label }}
  </button>
</template>

<script lang="ts" setup>
import "./button.css";
import { reactive, computed } from "vue";
type SizeType = "small" | "medium" | "large";
interface Iprops {
  label: string;
  primary?: boolean;
  size?: SizeType;
  backgroundColor?: string;
}
const props = defineProps<Iprops>();
const { label, primary, backgroundColor, size } = reactive(props);
const emits = defineEmits(["click"]);
const classes = computed(() => ({
  "storybook-button": true,
  "storybook-button--primary": primary,
  "storybook-button--secondary": !primary,
  [`storybook-button--${size || "medium"}`]: true,
}));
const style = computed(() => ({ backgroundColor }));

const onClick = () => emits("click");
</script>
