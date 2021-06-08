<template>
  <div class="container">
    <div class=row>
      <div class="col-md-12">
        <h1 class="title">LoveLoveWedding大作戦2021 討伐リスト</h1>
        <b-table hover :items="items" :fields="fields"></b-table>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        fields: [
          {
            key: 'name',
            label: '討伐対象',
            sortable: false,
          },
          {
            key: 'exp',
            label: 'Base経験値',
            sortable: true,
          },
          {
            key: 'point',
            label: 'ブライダルポイント',
            sortable: true,
          },
          {
            key: 'start',
            label: '受注開始',
            sortable: true,
          },
          {
            key: 'place',
            label: '場所',
            sortable: true,
          },
          {
            key: 'lv',
            label: 'LV制限',
            sortable: true,
          }
        ],
        items: [
        ]
      }
    },
    mounted(){
      this.$axios.get(`https://api.steinhq.com/v1/storages/60bf188fd2a8585c5af281d1/2021.06`)
      .then((res) => {
        return this.items = res.data
      }).catch((e => {
        error({ searchPosts: e.response.status, message: e.message })
      }))
    }
  }
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  max-width: 1200px;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 700;
  font-size: 28px;
  color: #35495e;
  margin-top: 2em;
  margin-bottom: 2em;
  letter-spacing: 1px;
}

</style>
