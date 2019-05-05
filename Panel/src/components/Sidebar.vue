<template>
  <div>
    <div class="items">
      <div class="header">
        <div class="flag">
          <div><b>dooonut</b></div>
        </div>
      </div>
      <div style="margin-top: 80px">
        <ul class="nav" v-for="(item, index) in menu">
          <li :key="index" class="nav-item">
            <img :src="item.imgSrc" class="item-img">
            <span class="item-title">{{ item.title }}</span>

            <div v-if="item.arrow !== undefined" @click="show(index)">
              <img :src="item.arrow" :class="{'arrow': flag === index}" style="width: 18px; height: 18px; margin-left: 80px;">
            </div>
            <div v-else class="arrowHid"></div>

          </li>
          <transition name="fading">
            <ul v-if="item.arrow !== undefined && index === 0" v-show="count === index" class="nav-hidden">
              <li>New message</li>
              <li>Inbox</li>
              <li>Outbox</li>
            </ul>
          </transition>
          <transition name="fading">
            <ul v-if="item.arrow !== undefined && index === 1" v-show="count === index" class="nav-hidden">
              <li>Creat Invoice</li>
              <li>View All</li>
              <li>Manage Invoice</li>
            </ul>
          </transition>
        </ul>
      </div>
      <div class="customers">
        <ul class="tool-bar">
          <div class="title">
            CUSTOMERS
          </div>
          <li v-for="customer in customers">
            <div style="display: flex">
              <img :src="customer.headPhoto" class="head-photo">
              <div>
                <div class="name">{{ customer.name }}</div>
                <div class="job">{{ customer.job }}</div>
              </div>
            </div>
            <div class="number">
              {{ customer.fans }}
            </div>
          </li>
        </ul>
      </div>
      <div class="progress">
        <div>progress</div>
        <hr style="margin-top: 20px"/>
      </div>
      <div class="group">
        <img src="../../static/images/网络.svg">
        <img src="../../static/images/信息.svg">
        <img src="../../static/images/消息.svg">
        <div>
          <img class="usr" src="https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=2160840192,133594931&fm=27&gp=0.jpg">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Sidebar",
    data() {
      return {
        menu: [
          {
            imgSrc: '../static/images/message.svg',
            title: 'Message',
            arrow: '../static/images/arrow.svg',
          },
          {
            imgSrc: '../static/images/message.svg',
            title: 'Message',
            arrow: '../static/images/arrow.svg'
          },
          {
            imgSrc: '../static/images/message.svg',
            title: 'Message',
          },
          {
            imgSrc: '../static/images/message.svg',
            title: 'Message',
          },
          {
            imgSrc: '../static/images/message.svg',
            title: 'Message',
          },
          {
            imgSrc: '../static/images/message.svg',
            title: 'Message',
          },
          {
            imgSrc: '../static/images/message.svg',
            title: 'Message',
          },
          {
            imgSrc: '../static/images/message.svg',
            title: 'Message',
          },
        ],
        customers: [
          {
            headPhoto: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2883602379,3407073745&fm=27&gp=0.jpg',
            name: 'Fan Bingbing',
            job: 'actor',
            fans: '100k'
          },
          {
            headPhoto: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=1480806899,456620986&fm=15&gp=0.jpg',
            name: 'Zhao Liying',
            job: 'actor',
            fans: '100k'
          }
        ],
        flag: false,
        count: -1,
      }
    },
    methods: {
      show: function (ind) {
        if (this.count === ind) {
          this.count = -1
          this.flag = -1
        } else {
          this.count = ind
          this.flag = ind
        }

      }
    }
  }
</script>

<style scoped>
  @import "../assets/css/side-bar.css";
</style>
