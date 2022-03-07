<template>
  <img alt="Vue logo" src="./assets/logo.png">
    <div>
        <h1>{{count}}</h1>
        <h1>{{double}}</h1>
        <button @click="increase">👍点击加1</button>
    </div>
</template>

<script lang="ts">
import { defineComponent,ref,computed,reactive,toRefs } from 'vue';
interface dataProps{
    count:number;
    double:number;
    increase:() => void,
    numbers:[],
    person:{name?:string}//代表name属性是可选属性
}
export default defineComponent({
    name: 'App',
    setup(){
        // const count = ref(0);
        // const double = computed(()=>{
        //     return count.value * 2
        // })
        // const increase = () => {
        //     count.value++
        // }

        //下面是使用reactive
        const data:dataProps = reactive({
            count:0,
            increase:()=>{
                data.count ++
            },
            double:computed(()=>{
                return data.count * 2
            }),
            numbers:[1,2],
            person:{}
        })
        const refData = toRefs(data)
        return {
            // count,
            // increase,
            // double
            ...refData
        }
    }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
