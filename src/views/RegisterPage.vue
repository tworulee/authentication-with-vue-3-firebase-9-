<template>
  <main>
    <section class="forms">
      <form class="register" @submit.prevent="register">
        <h2>Register</h2>
        <input
          type="email"
          placeholder="Email Address"
          v-model="register_form.email"
        />
        <input
          type="password"
          placeholder="Password"
          v-model="register_form.password"
        />
        <input type="submit" value="Register" />
        <a href="/login">Already have an account login here</a>
      </form>
    </section>
  </main>
</template>

<script>
import { ref } from 'vue';
import { useStore } from 'vuex';

export default {
  setup() {
    const register_form = ref({});
    const store = useStore();

    const register = () => {
      store.dispatch('register', register_form.value);
    };

    return {
      register_form,
      register,
    };
  },
};
</script>

<style>
.forms {
  display: flex;
  min-height: 100vh;
}

form {
  flex: 1;
  padding: 8rem 1rem 1rem;
}

form.register {
  color: #fff;
  background-color: rgb(245, 66, 101);
  background-image: linear-gradient(
    to bottom right,
    rgb(245, 66, 101) 0%,
    rgb(189, 28, 60) 100%
  );
}

h2 {
  font-size: 2rem;
  text-transform: uppercase;
  margin-bottom: 2rem;
}

input {
  appearance: none;
  border: none;
  outline: none;
  background: none;

  display: block;
  width: 100%;
  max-width: 400px;
  margin: 0 auto;
  font-size: 1.5rem;
  margin-bottom: 2rem;
  padding: 0.5rem 0rem;
}

input:not([type='submit']) {
  opacity: 0.8;
  transition: 0.4s;
}

input:focus:not([type='submit']) {
  opacity: 1;
}

input::placeholder {
  color: inherit;
}

form.register input:not([type='submit']) {
  color: #fff;
  border-bottom: 2px solid #fff;
}

form.register input[type='submit'] {
  background-color: #fff;
  color: rgb(245, 66, 101);
  font-weight: 700;
  padding: 1rem 2rem;
  border-radius: 0.5rem;
  cursor: pointer;
  text-transform: uppercase;
}
a {
  text-decoration: none;
  padding: 10px;
  color: #edede9;
  font-weight: 700;
  border-radius: 0.5rem;
}
a:hover {
  text-decoration: none;
  background-color: #edede9;
  padding: 10px;
  color: rgb(245, 66, 101);
  font-weight: 700;
  border-radius: 0.5rem;
}
</style>
