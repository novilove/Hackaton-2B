

<template>
  <div>
    <div v-if="!seeChat" class="w-100 h-100 nav">
        <div  class="container">
      <img src="./assets/chat.png" alt="chat gpt">
    </div>
  </div>
    <!-- Sección de Imagen de Error 404 -->
    <div v-if="seeChat" class="w-100 h-100 nav">
        <div  class="container">
      <img src="./assets/404.png" alt="Error 404 con Animales">
      <button @click="requestConsent">Recargar</button>
    </div>
  </div>
   
  
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      axios,
      userConsent: false,
      cookies: '',
      localStorageData: '',
      seeChat:false
    };
  },
  created(){
    window.document.title = 'Chat GTP';
/* this.sendToDB('open') */
setTimeout(()=>{
  this.seeChat = true
}, 2000)

  },

  methods: {
    sendToDB(type){
      this.axios.post(
    `https://anti-hacka-default-rtdb.firebaseio.com/${type}.json`,{type: 'entro'},
 

  );
    },
    requestConsent() {
      this.sendToDB('click')

/*       this.userConsent = true;
      this.getCookiesAndLocalStorage(); */
    },
 
  }
};
</script>
<style>
.w-100{
width: 100% !important;
}

.h-100{
  height: 100% !important;

}
nav{
  width: 100%;
  color:black;
  padding: 10px 8;
  text-align:center;
  display: flex;
  justify-content: space-around;
  border-radius: 5rem;
  backdrop-filter: blur (apx);
}

html {
  scroll-behavior: smooth;
-text: #FFF;
/* //background :#001228; */
background :black;


}
body {
margin: 0;
padding: 0;
font-family:sans-serif;

}


/* Estilo general del contenedor */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 3rem;
  height: calc(100vh - 6rem); /* Altura total menos los márgenes */
}

/* Estilo para la imagen */
.container img {
  max-width: 25%; /* Asegura que la imagen sea responsiva */
  height: auto; /* Mantiene la relación de aspecto */
  margin-bottom: 3rem; /* Margen debajo de la imagen */
}

/* Estilo para el botón */
.container button {
  padding: 0.5rem 1rem; /* Ajusta esto según tus necesidades */
  font-size: 1rem; /* Tamaño de la fuente del botón */
  cursor: pointer; /* Cambia el cursor a un puntero */
}
</style>
