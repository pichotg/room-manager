<template>
  <div>
    <input type="number" v-model="roomNumber" placeholder="Room number" />
    <input type="number" v-model="numBeds" placeholder="Number of beds" />
    <select v-model="gender">
      <option value="male">Male</option>
      <option value="female">Female</option>
    </select>
    <button @click="registerRoom">Register Room</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      roomNumber: null,
      numBeds: null,
      gender: null,
    };
  },
  methods: {
    registerRoom() {
      const room = {
        roomNumber: this.roomNumber,
        numBeds: this.numBeds,
        gender: this.gender,
        occupiedBeds: 0,
      };
      let rooms = JSON.parse(localStorage.getItem('rooms')) || [];
      rooms.push(room);
      localStorage.setItem('rooms', JSON.stringify(rooms));
    },
  },
};
</script>
