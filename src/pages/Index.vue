<template>
  <q-page class="flex flex-center">
   
    <div class="controls-wrapper">
      <q-btn round size="4rem" color="primary"  class="play-btn-wrapper"  @click="control">
            <q-icon :name="playIcon">  </q-icon>
      </q-btn>
    </div>
       
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      player: new Audio(),
      isPlaying: false,
      radioUrl: 'https://smioradio.com:1145/stream'
    };
  },
   computed: {
   
    playIcon: function() {
      let self = this;
      return self.isPlaying ? "pause" : "play_arrow";
    }
  },
  methods: {
   control: function () {

     if(this.isPlaying) {
       this.pause()
     } else {
       this.play()
     }

   },
   play: function () {
    
      this.player.src = this.radioUrl;

      this.player.play()
      this.isPlaying = true;

   },
   pause: function ()  {

      this.player.pause()
      this.isPlaying = false;
      this.player.src = null;

   }


  }
};
</script>

<style>
.controls-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100vw;
  padding: 0 95px;
}


.play-btn-wrapper {

  box-shadow: 0 15px 41px 0 rgba(10, 31, 58, 0.53);
  cursor: pointer;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}

.play-icon {
  border: 0;
  background: transparent;
  width: 0;
  height: 19px;
  outline: 0;
  border-color: transparent transparent transparent #fff;
  transition: 100ms all ease;
  cursor: pointer;
  border-style: solid;
  border-width: 10px 0 10px 16px;
}

.paused {
  border-style: double;
  border-width: 0 0 0 15px;
}

.backward-btn {
  transform: rotate(180deg);
}
</style>
}
</script>
