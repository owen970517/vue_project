<template>
  <div class="menu">
    <a v-for="(header,i) in headers" :key="i">{{header}}</a>
  </div>
  <div class="modal" v-if="isModal==true" >
    <div class="modal-dis">
      <h4>상세페이지</h4>
      <p>{{selectedRoom}}</p>
      <button @click='closeModal'>닫기</button>
    </div>
  </div>
  <div v-for="(원룸,i) in 원룸들" :key="i" class="main">
    <img class='room-img' :src="원룸.image"/>
    <h4 @click='openModal(i)'>{{원룸.title}}</h4>
    <p> {{원룸.price}} 만원</p>
  </div>
</template>

<script>
import data from './assets/data'

export default {
  name: 'App',
  data() {
    return {
      원룸들 : data,
      products : [
        '역삼동',
        '천호동',
        '마포구'
      ],
      prices : [
        '123',
        '234',
        '345'
      ],
      headers : [
        'Home',
        'Product',
        'About'
      ],
      신고수 :[0,0,0],
      isModal : false,
      selectedRoom : null,
    }
  },
  methods : {
    openModal(i) {
      this.isModal = true;
      this.selectedRoom = this.원룸들[i].content
    },
    closeModal() {
      this.isModal =false
    }
  },
  components: {

  }
}
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.modal {
  width : 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}
.modal-dis {
  width: 100%;
  background: #fff;
  border-radius: 8px;
  padding: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding : 15px;
  border-radius: 5px;
  position: sticky;
  top: 0;
}
.menu a {
  color : #fff;
  padding: 10px;
}
.room-img {
  width : 100%;
  margin-top: 40px;
}
</style>
