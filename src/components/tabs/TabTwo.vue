<template>
  <v-col lg="12">
    <div class="tab-default">
      <v-tabs v-model="tab" flat hide-slider>
        <v-tab v-for="(item, index) in items" :key="index" :ripple="false">
          {{ item.name }}
        </v-tab>
      </v-tabs>

      <v-tabs-items v-model="tab">
        <v-tab-item
          transition="fade-transition"
          v-for="(item, index) in items"
          :key="index"
        >
          <v-card flat>
            <v-card-text>
              <div class="single-tab-content">
                <ul>

                  <li v-for="(detail, i) in item.details" :key="i">
                    <a
                      >{{ detail.title }}
                      <span v-if="detail.org"> - {{ detail.org }} </span>
                      <span v-if="detail.subtitle"> ({{detail.subtitle}}) </span>
                    </a>
                    <span v-if="!Array.isArray(detail.desc)">
                      {{ detail.desc }}
                    </span>
                    <ul v-if="Array.isArray(detail.desc)" class="list-style--2">
                      <li v-for="(description, k) in detail.desc" :key="k">
                        {{ description }}
                      </li>
                    </ul>
                  </li>
                </ul>
              </div>
            </v-card-text>
          </v-card>
        </v-tab-item>
      </v-tabs-items>
    </div>
  </v-col>
</template>
<script>
  export default {
    props: {
      items: {
        type: Array,
        default: [],
      },
    },
    data() {
      return {
        tab: null,
      };
    },
  };
</script>
