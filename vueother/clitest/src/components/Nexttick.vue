<template>
    <div id="nextt">
        <div class="wrapper" @click="Change">{{message}}</div> 
    </div>
</template>

<script>
export default {
    name: "nextt",
    props: [],
    data() {
        return {
            message: 1
        }
    },
    computed: {
        
    },
    watch: {
        
    },
    methods: {
        Change(){
            this.message = 'new message';
            // 此时并没有及时更新，等待dom完全更新后要使用$nextTick
            console.error("27行》》》",this.$el.textContent === 'new message') // false
            this.$nextTick(function () {
                console.log("nextTick中，29行》》》",this.$el.textContent === 'new message') // true
            })
        }
    },

    // 生命周期钩子函数
    mounted() {
        
    },
    created() {
        
    },

}
</script>

<style scoped>
.wrapper{
    border: 1px solid #cccccc;
}
</style>


