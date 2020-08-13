<template>
  <div class="container">
    <br /><br />
    <div id="home">
      <b-form @submit="onSubmit" @reset="onReset" v-if="show">
        <b-form-group id="input-group-1" label="FristName:" label-for="input-1">
          <b-form-input
            id="input-1"
            v-model="form.fristname"
            required
            placeholder="FristName"
          ></b-form-input>
        </b-form-group>

        <b-form-group id="input-group-2" label="LastName:" label-for="input-2">
          <b-form-input
            id="input-2"
            v-model="form.lastname"
            required
            placeholder="LastName"
          ></b-form-input>
        </b-form-group>
        <b-form-group
          id="input-group-3"
          label="Email address:"
          label-for="input-3"
        >
          <b-form-input
            id="input-3"
            v-model="form.email"
            type="email"
            required
            placeholder="Enter email"
          ></b-form-input>
        </b-form-group>

        <label for="datepicker-full-width">Birthday</label>
        <b-form-datepicker
          id="datepicker-full-width"
          v-model="form.birthday"
          menu-class="w-100"
          calendar-width="100%"
          class="mb-2"
        ></b-form-datepicker>        
        <b-button type="submit" variant="primary" style="margin-bottom:10px;">Add employee</b-button>
      </b-form>

      <div>
        <b-table striped hover :items="items"></b-table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { Firtname: "", Lastname: "", Birthday: "", Email: "", Operation: "" }
      ],
      form: {
        firtname: "",
        Lastname: "",
        email: "",
        birthday: ""
      },
      foods: [
        { text: "Select One", value: null },
        "Carrots",
        "Beans",
        "Tomatoes",
        "Corn"
      ],
      show: true
    };
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset(evt) {
      evt.preventDefault();
      // Reset our form values
      this.form.email = "";
      this.form.name = "";
      this.form.food = null;
      this.form.checked = [];
      // Trick to reset/clear native browser form validation state
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    }
  }
};
</script>

<style></style>
