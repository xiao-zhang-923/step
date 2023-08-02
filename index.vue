<template>
  <div class="stepFlex" :style="{ width: `${width}px` }">
    <div class="step_item" :style="{ flex: list.length }"
      :class="{ 'active': step == (index + 1), /* 'success': step > (index + 1) */ }" v-for="(item, index) in list"
      :key="index">
      <div class="step_item_number">
        <template v-if="!(step > (index + 1))">{{ index + 1 }}</template>
        <template v-if="(step > (index + 1))">
          <svg t="1690883422271" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
            p-id="3142" width="200" height="200">
            <path
              d="M503.808 47.104C248.832 47.104 40.96 254.976 40.96 509.952S248.832 972.8 503.808 972.8s462.848-207.872 462.848-462.848S758.784 47.104 503.808 47.104z m0 873.472c-226.304 0-410.624-184.32-410.624-410.624s184.32-410.624 410.624-410.624 410.624 184.32 410.624 410.624c-1.024 226.304-184.32 410.624-410.624 410.624z"
              fill="#4799EB" p-id="3143"></path>
            <path
              d="M701.44 358.4L434.176 625.664l-122.88-122.88c-12.288-12.288-32.768-12.288-45.056 0-12.288 12.288-12.288 32.768 0 45.056l144.384 144.384c6.144 6.144 15.36 9.216 23.552 9.216 8.192 0 17.408-3.072 23.552-9.216l288.768-288.768c12.288-12.288 12.288-32.768 0-45.056-12.288-12.288-32.768-12.288-45.056 0z"
              fill="#4799EB" p-id="3144"></path>
          </svg>
        </template>
      </div>
      <div class="step_item_title">{{ item.title }}</div>
      <div class="step_item_line" v-if="(index + 1) != list.length"></div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, PropType } from "vue";
interface StepItem {
  title?: string;
}
export default defineComponent({
  name: "Step",
  props: {
    width: {
      type: Number,
      default: 100,
    },
    step: {
      type: Number,
      default: 1,
    },
    list: {
      type: Array as PropType<StepItem[]>,
      default: () => [],
    },
  },
});
</script>
<style  lang="scss" scoped>
.stepFlex {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  margin: 32px auto 8px;

  .step_item {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;

    .step_item_number {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      font-size: 18px;
      background-color: #C2CCD6;
      color: #fff;
      line-height: 32px;
      text-align: center;
      margin-right: 8px;

      svg {
        width: 32px;
        height: 32px;
      }
    }

    .step_item_title {
      color: #C2CCD6;
      font-weight: 400;
      font-size: 14px;
    }

    .step_item_line {
      flex: 1;
      height: 1px;
      background-color: #E4EBF1;
      margin: 0 20px;
    }

    &:last-child {
      flex-basis: auto !important;
      flex-shrink: 0 !important;
      flex-grow: 0 !important;

      .step_item_line {
        width: 0;
        flex: 0;
      }
    }
  }

  .active {
    .step_item_number {
      background-color: #4799EB;
      color: #fff;
    }

    .step_item_title {
      color: #33404D;
    }
  }

  .success {
    .step_item_number {
      background: none !important;
    }

    .step_item_title {
      color: #4799EB;
    }
  }
}
</style>
