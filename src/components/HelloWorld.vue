<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{URL}} Links</h2>
		<p v-for="(item,index) in dataList">{{item.id}} -- {{item.body}}</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
			URL: process.env.url_api,
			dataList:[]
    }
  },
	methods:{
		ajaxs:function(){
			this.$axios.get('http://jsonplaceholder.typicode.com/posts?userId=1').then((res)=>{
				console.log(res)
				this.dataList = res.data;
				console.log(this.dataList)
			}).cathc((res)=>{
				console.log('错误')
			})
		}
	},
	mounted() {
		this.ajaxs();
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
