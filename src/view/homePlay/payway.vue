<template>
  <div class="">
    <div class="pay-page" >
        <div class="pay-info">
          <span class="pay-tel" >为<b>{{tel}}</b>充值</span>
          <span class="pay-price"><small>￥</small><i>{{price}}</i></span>
          <span class="pay-wraing">请在提交订单后<i class="three">30分钟内</i>完成支付，否则系统会自动取消订单</span>
        </div>
        <h3>请选择支付方式</h3>
        <div class="pay-way">
          <li v-for="(item,index) in pay" @click="showico(item,index)">
                <img :src="item.img1" class="img1">
                <div class="payway-left">
                  <span>{{item.payname}}</span>
                  <span>{{item.paycontent}}</span>
                </div>
              <img :src="item.img2" alt="icon" class="img2" v-if="item.isshow">

          </li>
          <div style="clear:both"></div>
          <span class="pay-affirm" @click="paysure">确认支付<small class="btnmoney">￥</small><i  class="btn-price">{{price1}}</i></span>
        </div>
      </div>
  </div>
</template>
<script type="text/javascript">

    export default {
        data(){
         return {
           telok:false,
              pay:[
                    {img1:"../../.././static/img/bank.png",payname:"银行卡支付",paycontent:"支持超过100家银行信用卡借记卡",img2:"../../.././static/img/deposite/img/yes.png",isshow:true},
                    {img1:"../../.././static/img/zhifubao.png",payname:"支付宝支付",paycontent:"全球领先，超过4.5亿用户的选择",img2:"../../.././static/img/deposite/img/yes.png",isshow:false},
                    {img1:"../../.././static/img/wx.png",payname:"微信支付",paycontent:"推荐4.2以上版本使用",img2:"../../.././static/img/deposite/img/yes.png",isshow:false}
                ],
               
                
            }
        },
        methods:{
            showico(item,index){
                for(let i=0;i<this.pay.length;i++){
                this.pay[i].isshow=false
                this.pay[index].isshow=true
                }
            },
            paysure(){
              
            }

        },
      mounted(){
        this.$store.state.backshow=true
      },
        computed:{
          tel(){
             if(this.$store.state.tel===''){
              return this.$store.state.depositetel
             }else{
               return this.$store.state.tel
             }
            
            },
            
          price(){
            return this.$store.state.depositeprice
          },
          price1(){
            return this.price*0.995
          }
        }
    }
</script>
<style scoped>

.pay-page{
  width:90%;
  margin:40px auto;
  padding:20px 0 60px 0;

}
.pay-info{
  width:100%;
  margin: 0 auto;
  text-align: center;
  background:#f5f5f5;
  padding-bottom:4px
}
.pay-info span{
  display:block
}
.pay-tel{
  background:#26A2FF;
  color:#fff
}
.pay-info .pay-tel{
  width:100%;
  height:30px;
  text-align: center;
  line-height: 30px;

}
.pay-price{
  color:red;
  font-size:18px;
  padding:15px 0;
  font-weight:bold
}
small{
  font-size:12px;
  color:red
}
.pay-wraing{
  font-size:12px;
   color:#666;
}
i{
  font-style: normal;
  color:red;
  font-size:18px
}
.three{
  font-size:12px
}
h3{
  width:100%;
  height:40px;
  line-height: 40px;
  color:#666;
  margin-top:10px
}
.pay-way li{
  display:block;
  height:60px;
  padding-top: 10px;
  position:relative;
  border-top:1px solid #ccc;
  border-bottom:1px solid #ccc
}
.pay-way li:nth-child(2),.pay-way li:nth-child(3){
  border-top:none
}
.pay-way li span:nth-child(2){
  font-size:12px;
  margin-top:20px;
}
.pay-way li .img1{
    display: inline-block;
    width: 30px;
    height: 30px;
    padding:0 5px;
    vertical-align: top;
}
.pay-way li .payway-left{
  display: inline-block;
}
.pay-way li .img2{
    position:absolute;
    right:0;
    top:40%;
    width: 20px;
    height: 20px;

}

.pay-way li span{
   display:block;
   margin-bottom:5px;
   text-align: left
}

.pay-affirm{
  display:block;
  height:40px;
  line-height: 40px;
  color:#fff;
  margin-top:10px;
  border-radius:3px;
  background:#26A2FF;
  text-align: center
}
.btn-price,.btnmoney{
  color:#fff
}
</style>
