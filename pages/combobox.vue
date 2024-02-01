<template>
  <div class="d-flex combobox-container d-flex">
    <div class="combobox">
      <v-combobox
        ref="comboboxTextField"
        v-model="value"
        :items="items"
        outlined
        @keydown.enter="handleKeyDownEnter"
      >
        <template #item="{ item: index, on: on, attrs: attrs }">
              <v-list-item
                :title="items[index]"
                class="clickable-row px-2 min-height-24"
                v-bind="attrs"
                v-on="on"
                @click="handleClickList"
              >
                <span>{{items[index]}}</span>
              </v-list-item>
        </template>
      </v-combobox>
    </div>
    <div class="text-box">
      <v-text-field ref="textBoxTextField" outlined></v-text-field>
    </div>
  </div>

</template>

<script>

export default {
  name: 'ComboboxPage',
  "$refs": {
    comboboxTextField: HTMLInputElement,
    textBoxTextField: HTMLInputElement
  },
  data() {
    return {
      items: ["", "1", "2", "3", "4", "5", "6", "7", "8", "9", "10"],
      value: ""
    }
  },
  methods: {
    handleKeyDownEnter() {
      this.value = this.tempValue
      this.$refs.comboboxTextField.blur()
      this.$refs.textBoxTextField.focus()
    },

    handleClickList() {
      console.log("click")
    }
  }
}
</script>

<style>
.combobox-container {
  width: 100%;
  height: 100%;
}

.combobox {
  width: 200px;
}

.text-box {
  width: 200px;
}

.clickable-row {
  text-align: right;
}

.min-height-24 {
  min-height: 24px
}


</style>
