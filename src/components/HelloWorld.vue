<template>
  <div class="timer">
      <header class="title">
        <h1>Boxing rounds timer</h1>
      </header>
      <main class="timer-ui">
        <div class="round flex">
          <h2>Round Time</h2>
          <div class="round_time info-text">{{workTime}}</div>
          <div class="round_buttons">
            <button class="plus">+</button>
            <button class="minus">-</button>
          </div>
        </div>
        <div class="rest flex">
          <h2>Rest Time</h2>
          <div class="rest_time info-text">01:00</div>
          <div class="rest_buttons">
            <button class="plus">+</button>
            <button class="minus">-</button>
          </div>
        </div>
        <div class="number flex">
          <h2>Round total</h2>
          <div class="number_current info-text">{{rounds}}</div>
          <div class="number_buttons">
            <button @click="rounds+=1" class="plus">+</button>
            <button @click="rounds-=1" class="minus">-</button>
          </div>
        </div>
        <div class="start">
          <button @click="tick" class="start-btn">Start</button>
        </div>
      </main>
      <section class="display">{{setDisplayTime}}</section>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      rounds: 1,
      restTime: 60,
      workTime: 180,
      time: "03:00",
      work: false,
      timerId: Number
    };
  },
  methods: {
    tick() {
      this.work = !this.work;
      if (this.work) {
        this.timerId = setInterval(() => {
          this.workTime -= 1;
        }, 1000);
      } else if (!this.work) {
        clearInterval(this.timerId);
      }
    }
  },
  computed: {
    setDisplayTime() {
      let minutes = Math.trunc(this.workTime / 60);
      let seconds = this.workTime - minutes * 60;
      return `${minutes} : ${seconds}`;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2,
.info-text {
  color: azure;
}
h2 {
  text-transform: uppercase;
}
.info-text {
  font-size: 4vh;
}
.title {
  background-color: crimson;
  padding: 5px 0;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.2);
}
.flex {
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.timer-ui {
  padding: 20px;
  background-color: #41b883;
}

.start-btn {
  padding: 15px;
  background-color: crimson;
  width: 50%;
  border: none;
  font-size: 3vh;
  text-transform: uppercase;
  font-weight: bold;
  color: azure;
}
</style>
