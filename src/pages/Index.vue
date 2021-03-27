<template>
  <q-page class="q-mt-md">
    <q-card>
      <q-tab-panels v-model="tab" animated>
        <q-tab-panel name="resi">
          <q-input outlined v-model="awb" label="No Resi" class="q-mb-md" />
          <q-select
            outlined
            v-model="courier"
            :options="couriers"
            label="Pilih Kurir"
            class="q-mb-md"
          >
          </q-select>
          <q-btn label="Cek" class="full-width" color="primary" />
        </q-tab-panel>

        <q-tab-panel name="ongkir">
          <q-select
            outlined
            v-model="origin"
            :options="cities"
            label="Kota Asal"
            class="q-mb-md"
          />
          <q-select
            outlined
            v-model="destination"
            :options="cities"
            label="Kota Tujuan"
            class="q-mb-md"
          />
          <q-input
            outlined
            type="number"
            v-model="weight"
            label="Berat"
            class="q-mb-md"
          />
          <q-select
            outlined
            v-model="courierSelected"
            :options="couriers"
            label="Kurir"
            multiple
            class="q-mb-md"
          />
          <q-btn label="Cek" class="full-width" color="primary" />
        </q-tab-panel>
      </q-tab-panels>
    </q-card>
    <q-footer bordered class="bg-white text-primary">
      <q-tabs active-color="primary" class="text-grey" v-model="tab">
        <q-tab name="resi" label="Cek Resi" />
        <q-tab name="ongkir" label="Cek Ongkir" />
      </q-tabs>
    </q-footer>
  </q-page>
</template>

<script>
const stringOptions = [
  { label: "JNE", value: "jne" },
  { label: "TIKI", value: "tiki" }
];
// ["Google", "Facebook", "Twitter", "Apple", "Oracle"];
export default {
  name: "PageIndex",

  data() {
    return {
      tab: "resi",
      awb: null,
      courier: null,
      origin: null,
      destination: null,
      cities: [
        { label: "JNE", value: "jne" },
        { label: "TIKI", value: "tiki" }
      ],
      weight: null,
      courierSelected: [],
      couriers: stringOptions
    };
  },
  methods: {
    filterFn(val, update, abort) {
      update(() => {
        const needle = val.toLowerCase();
        this.options = stringOptions.filter(
          v => v.label.toLowerCase().indexOf(needle) > -1
        );
      });
    }
  }
};
</script>
