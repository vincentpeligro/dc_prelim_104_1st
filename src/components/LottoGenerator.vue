<template>
    <div class="container">
        <img src="../assets/pcso-logo.png" alt="pcso-logo">
        <h1>My Lotto Generator</h1>
    </div>
    <button @click="generateNumbers()">Generate</button>
    <div class="container" v-if="showResults">
        <h3 v-for="random in randomArray" :key="random">
            {{random}}
        </h3>
    </div>

</template>

<script>
export default {
    data(){
        return {
            randomArray : [],
            showResults: false,
        }
    },
    methods : {
        generateNumbers(){
            
            const mySet = new Set();

            while(mySet.size < 6){
                let rand = Math.floor(Math.random() * 42)+1;
                mySet.add(rand);
            }
            this.randomArray.push(...mySet);
            this.showResults = true;
            if(this.randomArray.length > 6){
                this.randomArray = []
            }
            
        },
    }
}
</script>

<style scope>
    .container{
        display: flex;
        align-items: center;
        justify-content: center;
    }
    img{
        width: 100px;
    }
    h3{
        padding: 10px;
    }
    button{
        position: absolute;
        margin-top: 100px;
        margin-left: -30px;
        padding: 10px;
    }
</style>