<template>
  <div class="about">
    <h1 @click="test" style="cursor: pointer;">This is an about page</h1>
  </div>
</template>
<script setup>
  let obj = new Proxy(
    {},
    {
      get(target, prop,receiver) {
        console.log('get', target,prop,receiver,target==receiver)
        return prop in target ? target[prop] : 37
      },
    }
  )
  obj.a = 1
  const test = () => {
    console.log(obj.a)
  }
</script>
<style scoped>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
