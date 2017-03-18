<template>
	<div>
		<ul>
			<li>{{data}}<span></span></li>
		</ul>
	</div>
</template>
<script>
	module.exports = {
		data:function(){
			return{
				data:''
			}	
		},
		methods: {
			getChampionDetail: function() {
				//$routeParams $state
				this.$http.get("http://lolapi.games-cube.com/GetChampionDetail?champion_id=" + this.$route.params.id, {
					headers: {
						"DAIWAN-API-TOKEN": "69CFD-C4C72-CD76F-476B0"
					}
				}).then(function(data) {
					console.log(data)
					console.log(data.data.data[0])
					this.data = data.data.data[0].name
				})
			}
		},
		mounted:function(){
			this.getChampionDetail()
		}
	}
</script>