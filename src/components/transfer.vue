<template>
  <div>
    <a-transfer
      v-model:target-keys="targetKeys"
      v-model:selected-keys="selectedKeys"
      :data-source="mockData"
      :show-search
      :titles="[' Source', ' Target']"
      :render="(item) => item.title"
      @change="handleChange"
      @selectChange="handleSelectChange"
      @scroll="handleScroll"
      @search="handleSearch"
    />
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue';

const mockData = [];
for (let i = 0; i < 20; i++) {
  mockData.push({
    key: i.toString(),
    title: `content nr ${i + 1}`,
  });
}

export default defineComponent({
  data() {
    const disabled = ref(false);
    const targetKeys = ref([]);
    const selectedKeys = ref([]);
    const handleChange = (nextTargetKeys, direction, moveKeys) => {
      console.log('targetKeys: ', nextTargetKeys);
      console.log('direction: ', direction);
      console.log('moveKeys: ', moveKeys);
    };
    const handleSelectChange = (sourceSelectedKeys, targetSelectedKeys) => {
      console.log('sourceSelectedKeys: ', sourceSelectedKeys);
      console.log('targetSelectedKeys: ', targetSelectedKeys);
    };
    const handleScroll = (direction, e) => {
      console.log('direction:', direction);
      console.log('target:', e.target);
    };
    const handleSearch = (dir, value) => {
      console.log('search:', dir, value);
    };
    return {
      mockData,
      targetKeys,
      selectedKeys,
      disabled,
      handleChange,
      handleSelectChange,
      handleScroll,
    };
  },
});
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
