<template>
    <div>
      <div class="wrap">
        <div class="le"><img :src="img" alt=""></div>
        <div class="rl">
          <div class="test">
            <h2>诊断</h2>
            <div id="example-4">
              <div class="le1">
                <div>
              <input type="radio" id="one" value="1" v-model="picked" name="zd">
              <label for="one">视神经炎</label> </div> <div>
              <input type="radio" id="three" value="3" v-model="picked" name="zd">
               <label for="three">视乳头水肿</label></div>
                <div>
              <input type="radio" id="five" value="5" v-model="picked" name="zd">
              <label for="five">视神经萎缩</label> </div> </div>
              <div class="rl1"> <div>
              <input type="radio" id="two" value="2" v-model="picked" name="zd">
              <label for="two">前部缺血性视神经病变</label></div> <div>
              <input type="radio" id="four" value="4" v-model="picked" name="zd">
              <label for="four">视盘血管炎</label></div> <div>
              <input type="radio" id="six" value="6" v-model="picked" name="zd">
              <label for="six">其他</label> </div>
                </div>
            </div>
            <h3>标注内容</h3>
            <ul class="menu1" @click="caizhao">
              <li @click="menu2"><img :src='"static/la"+tu2+".png"' alt="">眼底彩照 </li>
                <ul class="menu2" v-show="show_menu2"  >
                  <li @click="menu3"><img :src='"static/la"+tu3+".png"' alt="">视盘
                  </li>
              <ul class="menu3" v-show="show_menu3">
                <li>充血&nbsp;&nbsp;
                  <input type="radio" id="y1" name="y12" value="1" v-model="picked1"><label for="y1">无</label>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" id="y2" value="2" name="y12" v-model="picked1"><label for="y2">有</label>
                </li>
                <section v-show="show1_1">
                  <h4>部位</h4>
                  <input type="radio" name="y12-1" value="1" v-model="picked1_1">全视盘&nbsp;&nbsp;<input type="radio" name="y12-1" value="2" v-model="picked1_1">上部&nbsp;&nbsp;<input type="radio" name="y12-1" value="3" v-model="picked1_1">下部
                </section>
                <li>水肿&nbsp;&nbsp;<input type="radio" id="y3" name="y34" value="3" v-model="picked2"><label for="y3">无</label>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" name="y34" id="y4" value="4" v-model="picked2"><label for="y4">有</label></li>
                <section v-show="show1_2">
                  <h4>部位</h4>
                  <input type="radio" name="y12-2" value="1" v-model="picked1_2">全视盘&nbsp;&nbsp;<input type="radio" name="y12-2" value="2" v-model="picked1_2">上部&nbsp;&nbsp;<input type="radio" name="y12-2" value="3" v-model="picked1_2">下部&nbsp;&nbsp;<input type="radio" name="y12-2" value="4" v-model="picked1_2">颞侧&nbsp;&nbsp;<input type="radio" name="y12-2" value="5" v-model="picked1_2">鼻侧
                  <h4>程度</h4>
                  <input type="radio" name="y12-3" value="1" v-model="picked1_3">轻度&nbsp;&nbsp;<input type="radio" name="y12-3" value="2" v-model="picked1_3">中度&nbsp;&nbsp;<input type="radio" name="y12-3" value="3" v-model="picked1_3">重度
                </section>
                <li>出血&nbsp;&nbsp;<input type="radio" id="y5" name="y56" value="5" v-model="picked3"><label for="y5">无</label>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" id="y6"  name="y56" value="6" v-model="picked3"><label for="y6">有</label></li>
                <section v-show="show1_3">
                  <h4>部位</h4>
                  <input type="radio" name="y12-4" value="1" v-model="picked1_4">视盘表面&nbsp;&nbsp;<input type="radio" name="y12-4" value="2" v-model="picked1_4">视盘周围
                </section>
                <li>边界&nbsp;&nbsp;<input type="radio" id="y7" value="7" name="y78" v-model="picked4"><label for="y7">清晰</label>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" id="y8" name="y78" value="8" v-model="picked4"><label for="y8">模糊</label></li>
                <section v-show="show1_4">
                  <h4>部位</h4>
                  <input type="radio" name="y12-5" value="1" v-model="picked1_5">全视盘&nbsp;&nbsp;<input type="radio" name="y12-5" value="2" v-model="picked1_5">上部&nbsp;&nbsp;<input type="radio" name="y12-5" value="3" v-model="picked1_5">下部&nbsp;&nbsp;<input type="radio" name="y12-5" value="4" v-model="picked1_5">颞侧&nbsp;&nbsp;<input type="radio" name="y12-5" value="5" v-model="picked1_5">鼻侧
                </section>
                <li>视盘色泽&nbsp;&nbsp;<input type="radio" id="y9" value="9" name="y90" v-model="picked5"><label for="y9">正常</label>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" id="y10" name="y90" value="10" v-model="picked5"><label for="y10">异常</label></li>
                <section v-show="show1_5">
                  <h4>部位</h4>
                  <input type="radio" name="y12-6" value="1" v-model="picked1_6">全视盘&nbsp;&nbsp;<input type="radio" name="y12-6" value="2" v-model="picked1_6">上部&nbsp;&nbsp;<input type="radio" name="y12-6" value="3" v-model="picked1_6">下部&nbsp;&nbsp;<input type="radio" name="y12-6" value="4" v-model="picked1_6">颞侧&nbsp;&nbsp;<input type="radio" name="y12-6" value="5" v-model="picked1_6">鼻侧
                  <h4>程度</h4>
                  <input type="radio" name="y12-7" value="1" v-model="picked1_7">色淡&nbsp;&nbsp;<input type="radio" name="y12-7" value="2" v-model="picked1_7">色灰白&nbsp;&nbsp;<input type="radio" name="y12-7" value="3" v-model="picked1_7">色苍白
                </section>
                <li>杯盘比&nbsp;&nbsp;<input type="radio" id="y11" value="11" name="y11" v-model="picked6"><label for="y11">0~0.3</label>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" id="y12" name="y11" value="12" v-model="picked6"><label for="y12">0.3~0.6</label>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" id="y13" value="13" v-model="picked6"><label for="y13">≥0.6</label></li>
                <li>盘沿切迹&nbsp;&nbsp;<input type="radio" id="y14" value="14" name="y14" v-model="picked7"><label for="y14">无</label>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" id="y15" value="15" name="y14" v-model="picked7"><label for="y15">有</label></li>
                <section v-show="show1_6">
                  <h4>部位</h4>
                  <input type="checkbox" name="y12-8" value="1" v-model="picked1_8">颞上部&nbsp;&nbsp;<input type="checkbox" name="y12-8" value="2" v-model="picked1_8">颞下部&nbsp;&nbsp;<input type="checkbox" name="y12-8" value="3" v-model="picked1_8">颞侧&nbsp;&nbsp;<input type="checkbox" name="y12-8" value="4" v-model="picked1_8">上方&nbsp;&nbsp;<input type="checkbox" name="y12-8" value="5" v-model="picked1_8">下方
                </section>
              </ul>
                  <li @click="sc1" > 黄斑&nbsp;&nbsp;<input type="radio" id="y16" name="y16" value="16" v-model="picked8"><label for="y16">正常</label>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" id="y17" value="17" name="y17" v-model="picked8"><label for="y17">病变</label></li>
                  <section v-show="show1_7">
                    <h4>表现</h4>
                    <input type="checkbox" name="y12-9" value="1" v-model="picked1_9">水肿&nbsp;&nbsp;<input type="checkbox" name="y12-9" value="2" v-model="picked1_9">浅脱离&nbsp;&nbsp;<input type="checkbox" name="y12-9" value="3" v-model="picked1_9">硬渗&nbsp;&nbsp;<input type="checkbox" name="y12-9" value="4" v-model="picked1_9">出血
                  </section>
                  <li @click="sc2" > 视网膜&nbsp;&nbsp;<input type="radio" id="y18" name="y18" value="18" v-model="picked9"><label for="y18">正常</label>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" id="y19" value="19" name="y19" v-model="picked9"><label for="y19">病变</label></li>
                  <section v-show="show1_8">
                    <h4>表现</h4>
                    <input type="checkbox" name="y12-10" value="1" v-model="picked1_10">水肿&nbsp;&nbsp;<input type="checkbox" name="y12-10" value="2" v-model="picked1_10">浅脱离&nbsp;&nbsp;<input type="checkbox" name="y12-10" value="3" v-model="picked1_10">硬渗&nbsp;&nbsp;<input type="checkbox" name="y12-10" value="4" v-model="picked1_10">出血
                  </section>
                  <li @click="sc3" ><img :src='"static/la"+tu6+".png"' alt="">视网膜血管</li>
                  <section v-show="show1_9">
                    <h4>动脉细</h4>
                    <input type="radio" name="y12-11" value="1" v-model="picked1_11">无&nbsp;&nbsp;<input type="radio" name="y12-11" value="2" v-model="picked1_11">有
                    <h4>静脉迂曲、扩张</h4>
                    <input type="radio" name="y12-12" value="1" v-model="picked1_12">无&nbsp;&nbsp;<input type="radio" name="y12-12" value="2" v-model="picked1_12">有
                  </section>
               </ul>
            </ul>
            <ul class="menu1-1" @click="shiye">
              <li @click="menu4"><img :src='"static/la"+tu7+".png"' alt="">视野</li>
              <ul>
                <li class="menu1-2"><div v-show="show_sy"><div style="padding-left: 40px">视野缺损&nbsp;&nbsp;<input type="radio" id="y1-1" name="y1-1" value="1" v-model="picked10"><label for="y1-1">无</label>  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input type="radio" id="y2-1" value="2" name="y1-1" v-model="picked10"><label for="y2-1">有</label></div>
                  <section v-show="show1_10">
                  <h4>视野缺损形态</h4>
                    <div class="xt">
                  <input type="checkbox" name="dx" value="1" v-model="myVal" />
                  <label>中心暗点</label><br>
                  <input type="checkbox" name="dx" value="2" v-model="myVal" />
                  <label>盲中心暗点</label><br>
                  <input type="checkbox" name="dx" value="3" v-model="myVal" />
                  <label>全盲</label><br>
                  <input type="checkbox" name="dx" value="4" v-model="myVal" />
                  <label>象限性视野缺损</label><br>
                  <section class="byy" v-show="show1_11">
                    <input type="radio" name="y12-13" value="1" v-model="picked1_13">与生理盲点相连&nbsp;&nbsp;<input type="radio" name="y12-13" value="2" v-model="picked1_13">与生理盲点不相连
                  </section>
                  <input type="checkbox" name="dx" value="5" v-model="myVal" />
                  <label>弓形暗点</label><br>
                  <section class="byy" v-show="show1_12">
                    <input type="radio" name="y12-14" value="1" v-model="picked1_14">与生理盲点相连&nbsp;&nbsp;<input type="radio" name="y12-14" value="2" v-model="picked1_14">与生理盲点不相连
                  </section>
                  <input type="checkbox" name="dx" value="6" v-model="myVal" />
                  <label>水平偏盲</label><br>
                  <section class="byy" v-show="show1_13">
                    <input type="radio" name="y12-15" value="1" v-model="picked1_15">上方&nbsp;&nbsp;<input type="radio" name="y12-15" value="2" v-model="picked1_15">下方
                  </section>
                  <input type="checkbox" name="dx" value="7" v-model="myVal" />
                  <label>垂直偏盲</label><br>
                  <section class="byy" v-show="show1_14">
                    <input type="radio" name="y12-16" value="1" v-model="picked1_16">颞侧&nbsp;&nbsp;<input type="radio" name="y12-16" value="2" v-model="picked1_16">鼻侧
                  </section>
                  <input type="checkbox" name="dx" value="8" v-model="myVal" />
                  <label>偏盲性中心暗点</label><br>
                  <input type="checkbox" name="dx" value="9" v-model="myVal" />
                  <label>旁中心暗点</label><br>
                  <input type="checkbox" name="dx" value="10" v-model="myVal" />
                  <label>鼻侧阶梯</label><br>
                  <input type="checkbox" name="dx" value="11" v-model="myVal" />
                  <label>环形暗点</label><br>
                  <input type="checkbox" name="dx" value="12" v-model="myVal" />
                  <label>管状视野</label><br>
                  <input type="checkbox" name="dx" value="13" v-model="myVal" />
                  <label>颞侧视岛</label><br>
                    </div>

                </section>
                </div>
                </li>

              </ul>
            </ul>
          </div>
        </div>
      </div>
      <footer>
        <button @click="prev">上一张</button>
        <button @click="xia">下一张</button>
        <div>
        <button>取消</button>
        <button id='btn' @click="sub()">保存</button>
        </div>
      </footer>
    </div>

</template>

<script>
  import axios from 'axios'
import $ from 'jquery'
  import qs from  'qs'
    export default {
        name: "index",
        data(){
          return{
            again:true,
            resourceSno:null,
            myVal:[],
            resourceId:0,
            hb:false,
            swm:false,
            tu3:1,
            tu1:1,
            tu2:1,

            tu6:1,
            tu7:1,
            img:'',
            picked:'' ,
            picked1:1,
            picked1_1:'',
            picked2:3,
            picked1_2:'',
            picked1_3:'',
            picked3:5,
            picked1_4:'',
            picked4:7,
            picked1_5:'',
            picked5:9,
            picked1_6:'',
            picked1_7:'',
            picked6:11,
            picked7:14,
            picked1_8:[],
            picked8:16,
            picked1_9:[],
            picked9:18,
            picked1_10:[],
            picked10:1,
            picked1_13:'',
            picked1_14:'',
            picked1_15:'',
            picked1_16:'',
            picked1_11:'',
            picked1_12:'',
            show_menu2:false,
            show_menu3:false,
            show_sy:false,
            show1_1:false,
            show1_2:false,
            show1_3:false,
            show1_4:false,
            show1_5:false,
            show1_6:false,
            show1_7:false,
            show1_8:false,
            show1_9:false,
            show1_10:false,
            show1_11:false,
            show1_12:false,
            show1_13:false,
            show1_14:false,
            fundus:'',
            view:''


          }
        },
      methods: {
          sub(){
            var that=this
              var data=[this.again,this.picked,this.picked1,this.picked2,this.picked3,this.picked4,this.picked5,this.picked6,this.picked7,this.picked8,this.picked9,this.picked10,this.picked1_1,this.picked1_2,this.picked1_3,this.picked1_4,this.picked1_5,this.picked1_6,this.picked1_7,this.picked1_8.toString(),this.picked1_9.toString(),this.picked1_10.toString(),this.picked1_11,this.picked1_12,this.picked1_13,this.picked1_14,this.picked1_15,this.picked1_16,this.myVal.toString()]
            data=qs.stringify(data)
            console.log(data)
            axios.post('http://dev.tagging.truthai.cn/api/record/addRecord', this.qs.stringify({
              resourceSno:that.resourceSno,
              diagnosisSno:that.resourceSno,
              taggingResult:data
            }))
              .then(function (response) {
                that.$message({
                  message: '保存成功',
                  type: 'success'
                });
                console.log(response);
              })
              .catch(function (error) {
                console.log(error);
              });
          },
          prev(){
            var that=this
            axios.get('http://dev.tagging.truthai.cn/api/resource/getPrevResource', {
              params: {
                resourceId:that.resourceId,
                sourceType:1
              }
            })
              .then(function (res) {
                var data=res.data.data
                if(data){
                  that.resourceId=data.resourceId
                  that.resourceSno=data.resourceSno
                  that.fundus=data.fundusPath
                  that.view=data.viewPath
                  that.img='http://dev.tagging.truthai.cn/api/resource/showImage?ossKey='+data.fundusPath
                  axios.get('http://dev.tagging.truthai.cn/api/record/getRecord', {
                    params: {
                      resourceSno:data.resourceSno,
                      diagnosisSno:data.resourceSno
                    }
                  })
                    .then(function (res) {
                      console.log(res)
                      if(res.data.data){
                        var re=res.data.data.taggingResult
                        re=qs.parse(re)
                        that.again=false
                        that.picked=re[1]
                        that.picked1=re[2]
                        that.picked2=re[3]
                        that.picked3=re[4]
                        that.picked4=re[5]
                        that.picked5=re[6]
                        that.picked6=re[7]
                        that.picked7=re[8]
                        that.picked8=re[9]
                        that.picked9=re[10]
                        that.picked10=re[11]
                        that.pick1_1=re[12]
                        that.pick1_2=re[13]
                        that.pick1_3=re[14]
                        that.pick1_4=re[15]
                        that.pick1_5=re[16]
                        that.pick1_6=re[17]
                        that.pick1_7=re[18]
                        that.pick1_8=re[19].split(',')
                        that.pick1_9=re[20].split(',')
                        that.pick1_10=re[21].split(',')
                        that.pick1_11=re[22]
                        that.pick1_12=re[23]
                        that.pick1_13=re[24]
                        that.pick1_14=re[25]
                        that.pick1_15=re[26]
                        that.pick1_16=re[27]
                        that.myVal=re[28].split(',')
                      }else{
                        that.again=true
                        that.picked=''
                        that.picked1=1
                        that.picked2=3
                        that.picked3=5
                        that.picked4=7
                        that.picked5=9
                        that.picked6=11
                        that.picked7=14
                        that.picked8=16
                        that.picked9=18
                        that.picked10=1
                        that.pick1_1=''
                        that.pick1_2=''
                        that.pick1_3=''
                        that.pick1_4=''
                        that.pick1_5=''
                        that.pick1_6=''
                        that.pick1_7=''
                        that.pick1_8=[]
                        that.pick1_9=[]
                        that.pick1_10=[]
                        that.pick1_11=''
                        that.pick1_12=''
                        that.pick1_13=''
                        that.pick1_14=''
                        that.pick1_15=''
                        that.pick1_16=''
                        that.myVal=[]
                      }
                    })
                    .catch(function (error) {
                      console.log(error);
                    });

                }
              })
              .catch(function (error) {
                console.log(error);
              });
          },
          xia(){
            var that=this
            axios.get('http://dev.tagging.truthai.cn/api/resource/getNextResource', {
              params: {
                resourceId:that.resourceId,
                sourceType:1
              }
            })
              .then(function (res) {
                var data=res.data.data
                if(data){
                  that.resourceId=data.resourceId
                  that.resourceSno=data.resourceSno
                  that.fundus=data.fundusPath
                  that.view=data.viewPath
                  that.img='http://dev.tagging.truthai.cn/api/resource/showImage?ossKey='+data.fundusPath
                  axios.get('http://dev.tagging.truthai.cn/api/record/getRecord', {
                    params: {
                      resourceSno:data.resourceSno,
                      diagnosisSno:data.resourceSno
                    }
                  })
                    .then(function (res) {
                      console.log(res)
                      if(res.data.data){
                        var re=res.data.data.taggingResult
                        re=qs.parse(re)
                        that.again=false
                        that.picked=re[1]
                        that.picked1=re[2]
                        that.picked2=re[3]
                        that.picked3=re[4]
                        that.picked4=re[5]
                        that.picked5=re[6]
                        that.picked6=re[7]
                        that.picked7=re[8]
                        that.picked8=re[9]
                        that.picked9=re[10]
                        that.picked10=re[11]
                        that.pick1_1=re[12]
                        that.pick1_2=re[13]
                        that.pick1_3=re[14]
                        that.pick1_4=re[15]
                        that.pick1_5=re[16]
                        that.pick1_6=re[17]
                        that.pick1_7=re[18]
                        that.pick1_8=re[19].split(',')
                        that.pick1_9=re[20].split(',')
                        that.pick1_10=re[21].split(',')
                        that.pick1_11=re[22]
                        that.pick1_12=re[23]
                        that.pick1_13=re[24]
                        that.pick1_14=re[25]
                        that.pick1_15=re[26]
                        that.pick1_16=re[27]
                        that.myVal=re[28].split(',')
                      }else{
                        that.again=true
                        that.picked=''
                        that.picked1=1
                        that.picked2=3
                        that.picked3=5
                        that.picked4=7
                        that.picked5=9
                        that.picked6=11
                        that.picked7=14
                        that.picked8=16
                        that.picked9=18
                        that.picked10=1
                        that.pick1_1=''
                        that.pick1_2=''
                        that.pick1_3=''
                        that.pick1_4=''
                        that.pick1_5=''
                        that.pick1_6=''
                        that.pick1_7=''
                        that.pick1_8=[]
                        that.pick1_9=[]
                        that.pick1_10=[]
                        that.pick1_11=''
                        that.pick1_12=''
                        that.pick1_13=''
                        that.pick1_14=''
                        that.pick1_15=''
                        that.pick1_16=''
                        that.myVal=[]
                      }
                    })
                    .catch(function (error) {
                      console.log(error);
                    });
                }

              })
              .catch(function (error) {
                console.log(error);
              });
          },
        caizhao(){
          this.img='http://dev.tagging.truthai.cn/api/resource/showImage?ossKey='+this.fundus
        },
        shiye(){
          this.img='http://dev.tagging.truthai.cn/api/resource/showImage?ossKey='+this.view
        },
        menu3() {
          this.show_menu3 = !this.show_menu3
          this.tu3=-this.tu3
        },
        menu2() {
          this.show_menu2 = !this.show_menu2
          this.tu2=-this.tu2
        },
        menu4(){
          this.tu7=-this.tu7
          this.show_sy=!this.show_sy
},
        sc1(){

          this.hb=!this.hb
        },
        sc2(){

          this.swm=!this.swm
        },
        sc3(){
          this.tu6=-this.tu6
          this.show1_9=!this.show1_9

        }

      },
      mounted(){
        if(document.body.clientHeight&&document.documentElement.clientHeight)
        {
          var clientHeight = (document.body.clientHeight<document.documentElement.clientHeight)?document.body.clientHeight:document.documentElement.clientHeight;
        }
        else
        {
          var clientHeight = (document.body.clientHeight>document.documentElement.clientHeight)?document.body.clientHeight:document.documentElement.clientHeight;
        }
        $('.wrap').css('height',clientHeight)
        $('.rl').css('height',parseInt(clientHeight)-50+'px')
          var that=this
        axios.get('http://dev.tagging.truthai.cn/api/resource/getNextResource', {
          params: {
            resourceId:that.resourceId,
            sourceType:1
          }
        })
          .then(function (res) {
             var data=res.data.data
            if(data){
              console.log(data)
              that.resourceId=data.resourceId
              that.resourceSno=data.resourceSno
              that.fundus=data.fundusPath
              that.view=data.viewPath
              that.img='http://dev.tagging.truthai.cn/api/resource/showImage?ossKey='+data.fundusPath
              axios.get('http://dev.tagging.truthai.cn/api/record/getRecord', {
                params: {
                  resourceSno:data.resourceSno,
                  diagnosisSno:data.resourceSno
                }
              })
                .then(function (res) {
                  if(res.data.data){
                    var re=res.data.data.taggingResult
                    console.log(qs.parse(re));
                    axios.get('http://dev.tagging.truthai.cn/api/record/getRecord', {
                      params: {
                        resourceSno:data.resourceSno,
                        diagnosisSno:data.resourceSno
                      }
                    })
                      .then(function (res) {
                        console.log(res)
                        if(res.data.data){
                          var re=res.data.data.taggingResult
                          re=qs.parse(re)
                          that.again=false
                          that.picked=re[1]
                          that.picked1=re[2]
                          that.picked2=re[3]
                          that.picked3=re[4]
                          that.picked4=re[5]
                          that.picked5=re[6]
                          that.picked6=re[7]
                          that.picked7=re[8]
                          that.picked8=re[9]
                          that.picked9=re[10]
                          that.picked10=re[11]
                          that.pick1_1=re[12]
                          that.pick1_2=re[13]
                          that.pick1_3=re[14]
                          that.pick1_4=re[15]
                          that.pick1_5=re[16]
                          that.pick1_6=re[17]
                          that.pick1_7=re[18]
                          that.pick1_8=re[19].split(',')
                          that.pick1_9=re[20].split(',')
                          that.pick1_10=re[21].split(',')
                          that.pick1_11=re[22]
                          that.pick1_12=re[23]
                          that.pick1_13=re[24]
                          that.pick1_14=re[25]
                          that.pick1_15=re[26]
                          that.pick1_16=re[27]
                          that.myVal=re[28].split(',')
                        }else{
                          that.again=true
                          that.picked=''
                          that.picked1=1
                          that.picked2=3
                          that.picked3=5
                          that.picked4=7
                          that.picked5=9
                          that.picked6=11
                          that.picked7=14
                          that.picked8=16
                          that.picked9=18
                          that.picked10=1
                          that.pick1_1=''
                          that.pick1_2=''
                          that.pick1_3=''
                          that.pick1_4=''
                          that.pick1_5=''
                          that.pick1_6=''
                          that.pick1_7=''
                          that.pick1_8=[]
                          that.pick1_9=[]
                          that.pick1_10=[]
                          that.pick1_11=''
                          that.pick1_12=''
                          that.pick1_13=''
                          that.pick1_14=''
                          that.pick1_15=''
                          that.pick1_16=''
                          that.myVal=[]
                        }
                      })
                      .catch(function (error) {
                        console.log(error);
                      });


                  }
                })
                .catch(function (error) {
                  console.log(error);
                });
            }
          })
          .catch(function (error) {
            console.log(error);
          });



        },
      watch:{
          picked1:function (n,o) {
            if(n==2){
              this.show1_1=true
            }else{
              this.show1_1=false
            }
          },
        picked2:function (n,o) {
          if(n==4){
            this.show1_2=true
          }else{
            this.show1_2=false
          }
        },
        picked3:function (n,o) {
          if(n==6){
            this.show1_3=true
          }else{
            this.show1_3=false
          }
        },
        picked4:function (n,o) {
          if(n==8){
            this.show1_4=true
          }else{
            this.show1_4=false
          }
        },
        picked5:function (n,o) {
          if(n==10){
            this.show1_5=true
          }else{
            this.show1_5=false
          }
        },
        picked7:function (n,o) {
          if(n==15){
            this.show1_6=true
          }else{
            this.show1_6=false
          }
        },
        picked8:function (n,o) {
          if(n==17){
            this.show1_7=true
          }else{
            this.show1_7=false
          }
        },
        picked9:function (n,o) {
          if(n==19){
            this.show1_8=true
          }else{
            this.show1_8=false
          }
        },
        picked10:function (n,o) {
          if(n==2){
            this.show1_10=true
          }else{
            this.show1_10=false
          }
        },
        myVal:function (n,o) {
          var arr=n
          if(arr.indexOf('4')!=-1){
             this.show1_11=true
          }else {
            this.show1_11=false
            this.picked1_13=''
          }
          if(arr.indexOf('5')!=-1){
            this.show1_12=true
          }else {
            this.show1_12=false
            this.picked1_14=''
          }
          if(arr.indexOf('6')!=-1){
            this.show1_13=true
          }else {
            this.show1_13=false
            this.picked1_15=''
          }
          if(arr.indexOf('7')!=-1){
            this.show1_14=true
          }else {
            this.show1_14=false
            this.picked1_16=''
          }

        }
      }



    }
</script>

<style >
  input{vertical-align:middle}
  li img{display: inline}
  *{font-family:PingFangSC-Medium;}
  li{list-style: none;font-size: 14px}
   .wrap{width:100%;height:100%;}
  .le{float:left;height:100%;width:75%;}
  .le1{float:left;height:100%;width:45%;}
  .le img{width:100%;height:100%;}
  .rl{float:right;width:25%;position: relative;overflow:auto;overflow-y:scroll;padding-bottom:100px}
  .rl1{float:right;width:55%;}
  h3,h2{height:40px;font-size:14px; font-weight:500;color:rgba(29,29,29,1);line-height:40px;text-indent:12px;border-bottom: 1px solid rgba(240,240,240,1)}
  #example-4{padding-left:30px;border-bottom:1px solid rgba(240,240,240,1);overflow: hidden }
  .le1 div{position: relative;}
  h3{border:0}
  .menu3 li div{background:rgba(235,235,235,1); display: none }
  .rl1 div{position: relative}
   #example-4 input{position: absolute;top:14px;left:0; }
   #example-4 label{padding-left:20px;width:56px;height:40px;font-size:14px; font-weight:400;color:rgba(29,29,29,1);line-height: 40px}
  .menu1 li{text-indent:30px;font-size: 14px;line-height: 40px;min-height: 40px;font-weight:500;color:rgba(29,29,29,1);}
  .menu2 li{text-indent:50px;font-weight:400;}
  .menu3 li{text-indent:62px;font-weight:400;}
.menu1>li{background: rgba(240,240,240,1);}
   .menu2>li:nth-of-type(1){background:rgba(235,235,235,1);}
  .menu2>li:nth-of-type(3){background:rgba(235,235,235,1);}
  .menu2>li:nth-of-type(2){background:rgba(240,240,240,1);}
  .menu2>li:nth-of-type(4){background:rgba(240,240,240,1);}
   .menu3>li:nth-of-type(1){background:rgba(240,240,240,1);}
  .menu3>li:nth-of-type(3){background:rgba(240,240,240,1);}.menu3>li:nth-of-type(5){background:rgba(240,240,240,1);}
  .menu3>li:nth-of-type(7){background:rgba(240,240,240,1);}
  .menu3>li:nth-of-type(2){background:rgba(235,235,235,1);}.menu3>li:nth-of-type(4){background:rgba(235,235,235,1);}
  .menu3>li:nth-of-type(6){background:rgba(235,235,235,1);}
  section{padding-left:62px;background:#999;font-size: 14px;}
  .byy{padding-left:20px}
  .menu1-2 div .xt{padding-left:40px;line-height: 20px}
   section h4{margin-left:-2px;line-height: 40px; }
   section input{line-height: 40px;text-indent: 62px}
  .menu1-1>li{text-indent:30px;font-size: 14px;line-height: 40px;min-height: 40px;font-weight:500;color:rgba(29,29,29,1);
    background:rgba(235,235,235,1);}
  .menu1-2{background:rgba(240,240,240,1)}
  .menu1-2 div{line-height: 40px;}
  .menu1-2 div section{padding-left:0;}
  .menu1-2 div section h4{background:rgba(235,235,235,1);text-indent: 40px;line-height:40px }
  footer{width:25%;height:30px;position:fixed;bottom: 0;right:0;background:#ccc;padding:10px 0;}
  footer>button:nth-child(1){height:28px;border-radius:2px;border:1px solid rgba(29,29,29,1);font-size: 14px;margin:0 10px }
  footer>button:nth-child(2){height:28px;border-radius:2px;border:1px solid rgba(29,29,29,1);font-size: 14px;}
footer div{float:right;}
#btn{float:right;margin-left: 5px;background: #65a0f7;color:#fff}
  #btn span{margin-top:-20px;}
  footer div button{width:70px;height:28px;border-radius:2px;border:0;font-size: 14px;background: #fff;float: left}
</style>


