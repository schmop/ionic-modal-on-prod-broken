<template>
  <ion-header>
    <ion-toolbar color="medium">
      <ion-title>
        Modal open test
        <ion-icon
          :icon="closeCircleOutline"
          color="dark"
          @click="dismiss()"
          style="float: right"
        />
      </ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content color="light">
    <ion-item-group>
      <ion-item>
        If you can read this, the modal open was successful!
      </ion-item>
    </ion-item-group>
  </ion-content>
  <ion-footer>
    <ion-toolbar>
      <ion-button color="primary" @click="dismiss()">
        <ion-icon :icon="addCircleOutline" slot="start" />
        Celebrate
      </ion-button>
      <ion-button color="light" @click="dismiss()">
        <ion-icon :icon="closeCircleOutline" slot="start" />
        Cancel
      </ion-button>
    </ion-toolbar>
  </ion-footer>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { addCircleOutline, closeCircleOutline } from "ionicons/icons";
import {
  IonItemGroup,
  IonItem,
  IonContent,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonIcon,
  IonButton,
  IonFooter,
  modalController,
} from "@ionic/vue";

const SomeModal = defineComponent({
  name: "SomeModal",
  components: {
    IonContent,
    IonToolbar,
    IonIcon,
    IonTitle,
    IonHeader,
    IonItemGroup,
    IonItem,
    IonButton,
    IonFooter,
  },
  data: () => ({
    addCircleOutline,
    closeCircleOutline,
  }),
  computed: {},
  created() {
      console.log("Component created");
  },
  mounted() {
      console.log("Component mounted", this);
  },
  methods: {
    dismiss() {
      modalController.dismiss();
    },
  },
});

export default SomeModal;

export async function openSomeModal() {
  const createSomeModal = await modalController.create({
    component: SomeModal,
  });
  createSomeModal.present();
  await createSomeModal.onDidDismiss();
}
</script>

<style scoped>
</style>