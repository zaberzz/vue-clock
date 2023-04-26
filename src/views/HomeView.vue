<script setup lang="ts"></script>
<template>
  <div class="datetime">
    <div class="datetime-container">
      <div class="date">{{ day }}-{{ month }}-{{ year }}</div>
      <div class="time">{{ hours }} : {{ minutes }} : {{ seconds }}</div>
      <div class="day">{{ weekday }}</div>
    </div>
  </div>
</template>
<script>
export default {
  const zeroPad = (num, places) => String(num).padStart(places, '0')
      const months = [
        'January',
        'February',
        'March',
        'April',
        'May',
        'June',
        'July',
        'August',
        'September',
        'October',
        'November',
        'December'
      ]
      const weekdays = [
        'Sunday',
        'Monday',
        'Tuesday',
        'Wednesday',
        'Thursday',
        'Friday',
        'Saturday'
      ]
  data() {
    return {
      hours: 0,
      minutes: 0,
      seconds: 0,
      day: 0,
      month: 0,
      year: 0,
      weekday: 0
    }
  },
  mounted() {
    setInterval(() => this.setTime(), 1000)
  },
  methods: {
    setTime() {
      const date = new Date()
      this.hours = zeroPad(date.getHours(), 2)
      this.minutes = zeroPad(date.getMinutes(), 2)
      this.seconds = zeroPad(date.getSeconds(), 2)
      this.day = date.getDate()
      this.month = months[date.getMonth()]
      this.year = date.getFullYear()
      this.weekday = weekdays[date.getDay()]
    }
  }
}
</script>

<style>
* {
  @apply m-0 p-0 box-border;
}
.datetime {
  @apply bg-dark-50 flex justify-center items-center h-screen font-serif;
}

.datetime-container {
  @apply text-white border-4 w-500px p-15 border-cyan-500 rounded-3xl hover:(bg-cyan-500 shadow shadow-purple-100 transition-all duration-150);
}

.date {
  @apply text-center text-3xl font-bold tracking-wider;
}
.time {
  @apply text-6xl font-bold flex justify-center items-center mb-6 mt-3;
}
.day {
  @apply text-center text-2xl font-bold;
}
</style>
