<template>
  <v-container>
    <h1 class="text-center">Create Your Menu</h1>
    <v-expansion-panels multiple class="mt-5">
      <v-expansion-panel v-for="(p, i) in section" :key="i">
        <v-expansion-panel-header>
          <h3><v-text-field placeholder="Ex: Breakfast" v-model="p.header"></v-text-field></h3>
        </v-expansion-panel-header>
        <v-expansion-panel-content>
          <ul style="list-style-type: none;">
            <li v-for="(item, index) in p.content" :key="index">
              <v-row>
              <v-col cols="12" md="2">
                <v-text-field label="Name" v-model="item.name" />
              </v-col>
              <v-col cols="12" md="7">
                <v-text-field label="Description" v-model="item.description" />
              </v-col>
              <v-col cols="12" md="2">
                <v-text-field label="Price" v-model="item.price" />
              </v-col>
              <v-col cols="12" md="1">
                <v-btn text @click="deleteRow(index, p.content)">x</v-btn>
              </v-col>
              </v-row>
            </li>
          </ul>
          <v-btn text small color="primary" @click="addRow(p)">Add New Item</v-btn>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
    <v-btn block color="secondary" class="mt-4" @click="addPanel"> Add Menu Section </v-btn>
    <v-btn block color="success" dark class="mt-4" @click="onSubmit">Create Menu</v-btn>
  </v-container>
</template>

<script>
export default {
  name: "CreateMenu",
  data: () => ({
    items: [],
    section: [],
    inputs: 0
  }),
  methods: {
    addRow(p){
      p.content.push({
        name: '',
        description: '',
        price: ''
      })
    },
    deleteRow(index, content){
      content.splice(index,1)
    },
    onSubmit(){
      console.log(this.section)
    },
    addPanel(){
      this.section.push({header: "", content: []})
    }
  }

};
</script>
