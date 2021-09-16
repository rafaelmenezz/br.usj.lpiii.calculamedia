<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-grid>
          <ion-row>
            <ion-col size="2">
              <ion-icon
                src="/assets/calculator-outline.svg"
                size="large"
                style="margin-left: 3%"
              >
              </ion-icon>
            </ion-col>
            <ion-col>
              <ion-title>Calculadora de Média</ion-title>
            </ion-col>
          </ion-row>
        </ion-grid>
      </ion-toolbar>
    </ion-header>

    <ion-content v-if="!resultado">
      <ion-card>
        <ion-img class="center" src="/assets/calculadora.gif"></ion-img>
        <ion-label style="text-align: center">
          <p style="margin-left: 5%; margin-right: 5%">
            Preencha abaixo com 3 números e clique em calcular para exibir a
            média.
          </p>
        </ion-label>
        <ion-card-content>
          <ion-grid>
            <ion-row>
              <ion-col class="lb-calc">
                <ion-label>1º número: </ion-label>
              </ion-col>

              <ion-col>
                <ion-input
                  class="text-num"
                  type="number"
                  v-model="n1"
                ></ion-input>
              </ion-col>
            </ion-row>

            <ion-row>
              <ion-col class="lb-calc">
                <ion-label>2º número: </ion-label>
              </ion-col>

              <ion-col>
                <ion-input
                  class="text-num"
                  type="number"
                  v-model="n2"
                ></ion-input>
              </ion-col>
            </ion-row>

            <ion-row>
              <ion-col size="6" class="lb-calc">
                <ion-label>3º número: </ion-label>
              </ion-col>
              <ion-col>
                <ion-input
                  class="text-num"
                  type="number"
                  v-model="n3"
                ></ion-input>
              </ion-col>
            </ion-row>

            <ion-row>
              <ion-col>
                <ion-button expand="block" @click.prevent="calculo()">
                  CALCULAR
                </ion-button>
              </ion-col>
            </ion-row>
          </ion-grid>
        </ion-card-content>
      </ion-card>
    </ion-content>

    <ion-content v-else>
      <ion-card fullscreen>
        <ion-card-header>
          <ion-card-title class="result-title">A média é</ion-card-title>
        </ion-card-header>

        <ion-card-content>
          <p class="result">{{ media }}</p>
          <ion-button expand="block" @click.prevent="voltarCalculo()"
            >Voltar</ion-button
          >
        </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
  IonRow,
  IonCol,
  IonButton,
  IonGrid,
  IonImg,
  IonInput,
  IonLabel,
  IonCard,
  IonCardContent,
  IonCardHeader,
  IonCardTitle,
  IonIcon,
} from "@ionic/vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Home",
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonRow,
    IonCol,
    IonButton,
    IonGrid,
    IonImg,
    IonInput,
    IonLabel,
    IonCard,
    IonCardContent,
    IonCardHeader,
    IonCardTitle,
    IonIcon,
  },
  data: () => {
    return {
      n1: "",
      n2: "",
      n3: "",
      media: 0,
      resultado: false,
    };
  },
  methods: {
    calculo() {
      let x = 0;
      x += parseInt(this.n1);
      x += parseInt(this.n2);
      x += parseInt(this.n3);
      this.media = x / 3;

      /* Funciona, porém a conta da errada 
      this.media = parseInt(this.n1) + parseInt(this.n2) + parseInt(this.n3) / 3 
      */

      /* Iniciando as váriaveis com 0. Funciona, porém a conta da errada 
     this.media = this.n1 + this.n2 + this.n3 / 3
      */

      /* Iniciando as váriaveis com Number aparece um erro com NumberConstruct
       */

      this.alteraResult();
    },
    voltarCalculo() {
      this.n1 = "";
      this.n2 = "";
      this.n3 = "";
      this.alteraResult();
    },
    alteraResult() {
      this.resultado = !this.resultado;
    },
  },
});
</script>

<style scoped>
#container {
  text-align: center;

  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;

  color: #8c8c8c;

  margin: 0;
}

#container a {
  text-decoration: none;
}
.text-num {
  text-align: left;
}
.result-title,
.result {
  text-align: center;
}
.result-title {
  font-size: 2em;
}
.result {
  font-size: 200%;
}
.lb-calc {
  margin-top: 10px;
  text-align: right;
}
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 220px;
}
</style>