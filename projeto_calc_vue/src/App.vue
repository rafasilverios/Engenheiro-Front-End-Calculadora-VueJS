<script setup>
import { reactive } from 'vue';
import { ref } from 'vue';

const calc = reactive({
  n1: 0,
  n2: 0,
  resultado: '',
});

const selecao = ref('default');

const operacoes = {
  somar: (n1, n2) => n1 + n2,
  subtrair: (n1, n2) => n1 - n2,
  multiplicar: (n1, n2) => n1 * n2,
  dividir: (n1, n2) => n1 / n2,
};

function calcular() {
  const operacaoFn = operacoes[selecao.value];
  if (operacaoFn) {
    return operacaoFn(calc.n1, calc.n2);
  }
  return '';
}
</script>

<template>
  <body>
    <div class="container">
      <header>
        <h1>Calculadora Aritmética</h1>
      </header>
      <form>
        <input v-model.number="calc.n1" type="number" required placeholder="Digite o primeiro número">
        <input v-model.number="calc.n2" type="number" required placeholder="Digite o segundo número">
        <select v-model="selecao">
          <option value="default" selected>---</option>
          <option value="somar">somar</option>
          <option value="subtrair">subtrair</option>
          <option value="multiplicar">multiplicar</option>
          <option value="dividir">dividir</option>
        </select>
      </form>
      <div class="df-center">
        <h2>{{ calcular() }}</h2>
      </div>
    </div>    
    </body>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Roboto, sans-serif;
  color: #000;
}

.fs-15 {
  font-size: 15px;
}

.fs-24 {
  font-size: 24px;
}

.fs-26 {
  font-size: 26px;
}

body {
  margin: -8px;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #3D91C1, #DE3A83);
}

h2 {
  margin-top: 64px;
  color: #fff;
}

.df-center{
  display: flex;
  justify-content: center;
}

.container {
    display: block;
}

header {
    display: flex;
    justify-content: center;
    margin-bottom: 40px;
}

header h1 {
    margin-top: 20px;
    font-size: 40px;
    color: #fff;
}

form {
    display: flex;
    justify-content: center;
}

input, button, select {
    border-radius: 4px;
    padding: 12px;
    font-size: 18px;
}

select {
    max-width: 150px;
    margin-right: 8px;
    border: 1px solid #fff;
    outline-color: #fff;
    background-color: transparent;
    color: #fff;
}

input {
    max-width: 150px;
    margin-right: 8px;
    border: 1px solid #fff;
    outline-color: #fff;
    background-color: transparent;
    color: #fff;
}

::-webkit-input-placeholder {
    color: #fff;
}
  
:-moz-placeholder {
    color: #fff;
}
  
::-moz-placeholder {
    color: #fff;
}
  
:-ms-input-placeholder {
    color: #fff;
}
  

button {
  min-width: 60px;
  margin-right: 8px;
  border: 1px solid #fff;
  color: #fff;
  background-color: transparent;
  font-weight: bold;
  text-transform: uppercase;
  transition: all ease .5s;
}

button:hover {
  background-color: #fff;
  color: #707070;
}

ul {
    margin-top: 40px;
    margin-bottom: 20px;
    display: grid;
    justify-content: center;
}

ul li {
    border-radius: 4px;
    padding: 16px;
    margin: 4px 0;
    width: 460px;
    background-color: #fff;
    list-style-type: none;
    text-align: start;
    cursor: pointer;
}

.line-through {
    text-decoration: line-through;
}
</style>
