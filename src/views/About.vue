<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p v-for="item in newsList">{{item.class_name}}</p>
  </div>
</template>
<script>
    // @ is an alias to /src
    export default {
        name: 'about',
        data () {
            return {
                newsList: null
            }
        },
        methods:{
            getNewsList(){
                this.axios.get('http://10.3.129.23/backend/api.php/Major/majors').then((response)=>{
                    this.newsList=response.data.data;
                }).catch((response)=>{
                    console.log(response);
                })
            }
        },
        mounted () {
            this.getNewsList();
        }
    }
</script>