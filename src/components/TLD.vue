<template>
  <div>
    <div class="search-wrapper">
      <input v-model.trim="search" placeholder="filter" v-on:input="filter">
    </div>
    <span class="number">Found {{domains.length}} TLD's</span>
    <ul>
      <li v-for="(tld, index) in domains" :key="index">
        <a :href="'https://icannwiki.org/.' + tld.toLowerCase()" target="_blank">
          <span>{{tld}}</span>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
import tld from '../tld.json'
export default {
  name: 'HelloWorld',
  data() {
    return {
      search: '',
      domains: tld
    }
  },
  methods: {
    normalize(text) {
      return text.trim().toLowerCase()
    },
    filter() {
      this.domains = tld.filter(t =>
        this.normalize(t).includes(this.normalize(this.search.replace('.', '')))
      )
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.search-wrapper {
  background-image: url('../assets/bg.svg');
  background-color: #ffffff;
  border-radius: 3px;
  height: 400px;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: flex-end;
  background-size: cover;
  box-shadow: 0 8px 22px 0 rgba(0, 0, 0, 0.05);

  input {
    border: none;
    border-bottom: 2px solid #e1e1e1;
    width: 330px;
    padding-bottom: 12px;
    font-weight: 800;
    font-size: 54px;
    color: #4b4b4b;
    letter-spacing: 0;
    text-align: center;
    background: transparent;
    margin-bottom: 80px;
  }
}

.number {
  font-weight: 500;
  font-size: 24px;
  color: #b2a4ff;
  letter-spacing: 0;
  margin: 40px 0;
  display: inline-block;
  position: relative;

  &:after {
    content: '';
    background: #6db0ff;
    border-radius: 3px;
    height: 4px;
    width: 100%;
    display: block;
    position: absolute;
    margin-top: 5px;
  }
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;

  li {
    background: #ffffff;
    box-shadow: 0 8px 22px 0 rgba(0, 0, 0, 0.05);
    border-radius: 3px;
    margin-bottom: 30px;
    height: 100px;
    text-align: center;
    display: flex;
    align-items: center;
    padding-left: 40px;

    a {
      text-decoration: none;

      span {
        font-weight: 800;
        font-size: 54px;
        color: #4b4b4b;
        letter-spacing: 0;
        text-align: center;
        position: relative;

        @media screen and (max-width: 700px) {
          font-size: 24px;
        }

        &:after {
          content: '';
          background: #6db0ff;
          box-shadow: 0 6px 12px 0 rgba(109, 176, 255, 0.2);
          border-radius: 3px;
          height: 4px;
          width: 100%;
          display: block;
          position: absolute;
        margin-top: 19px;
        }
      &:after {
        content: '';
        background: #6db0ff;
        box-shadow: 0 6px 12px 0 rgba(109, 176, 255, 0.2);
        border-radius: 3px;
        height: 4px;
        width: 100%;
        display: block;
        position: absolute;
        margin-top: 19px;
      }
    }
  }
}
</style>
