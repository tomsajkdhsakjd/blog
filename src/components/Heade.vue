<template>
 
   <div id="header" class="header bg-white">
    <div class="navbar-container">
        <a href="#" class="navbar-logo">
            <img src="../assets/imgs/8.png" alt="神的孩子"/>
        </a>
        <div class="navbar-menu">
            <a v-for="item in headerdata " href="javascript:void(0);" @click="handlecategoryclick(item.category)">{{item.category}}</a>
           
              <router-link :to="'/aboutblog/'">关于本站</router-link>
            <router-link :to="'/Links/'">友情链接</router-link>
            
        </div>
     
        <div class="navbar-mobile-menu" onclick="">
            <span class="icon-menu cross"><span class="middle"></span></span>
            <ul>
                <li> <a v-for="item in headerdata " href="javascript:void(0);" @click="handlecategoryclick(item.category)">{{item.category}}</a>
           </li>
               
                 <li> <router-link :to="'/aboutblog/'">关于本站</router-link></li>
                  <li><router-link :to="'/Links/'">友情链接</router-link></li>
            </ul>
        </div>
    </div>
</div>

</template>
<script>
export default {
  name: 'Heade',
   data (){
    return {
      searchcontent:null
    }
  },
  props:{
    headerdata:Array
  },
  methods:{
    handlecategoryclick:function(Category){
     this.$store.commit('changecategory',Category)
     this.$router.push('/')
    },
     show:function(ev){
       if(ev.keyCode == 13&&this.searchcontent!=null){
          axios.get('http://admin.shendehaizi.com:8088/Category/search?searchcontent='+this.searchcontent).then(this.getsuccda)

    }
  },
     getsuccda:function(res){
      res=res.data   
      if(res!=null&&res.ok){
        var searchdata=res
        this.$emit('searcharticle',searchdata)
      }          

    }
  }
}
</script>

<style scoped>
@import "../assets/common/common.css";
.hljs{display:block;overflow-x:auto;padding:0.5em;background:#fff;color:black}
.hljs-comment,.hljs-quote{color:#006a00}.hljs-keyword,.hljs-selector-tag,.hljs-literal{color:#aa0d91}.hljs-name{color:#008}.hljs-variable,.hljs-template-variable{color:#660}.hljs-string{color:#c41a16}.hljs-regexp,.hljs-link{color:#080}.hljs-title,.hljs-tag,.hljs-symbol,.hljs-bullet,.hljs-number,.hljs-meta{color:#1c00cf}.hljs-section,.hljs-class .hljs-title,.hljs-type,.hljs-attr,.hljs-built_in,.hljs-builtin-name,.hljs-params{color:#5c2699}.hljs-attribute,.hljs-subst{color:#000}.hljs-formula{background-color:#eee;font-style:italic}.hljs-addition{background-color:#baeeba}.hljs-deletion{background-color:#ffc8bd}.hljs-selector-id,.hljs-selector-class{color:#9b703f}.hljs-doctag,.hljs-strong{font-weight:bold}.hljs-emphasis{font-style:italic}

</style>
