<template>
    <div id="app">
        <StyleEditor ref="styleEditor" :code="currentStyle"></StyleEditor>
        <ResumeEditor ref="resumeEditor" :markdown="currentMarkdown" :enableHtml="enableHtml"></ResumeEditor>
    </div>
</template>
<script>
import StyleEditor from './components/StyleEditor'
import ResumeEditor from './components/ResumeEditor'
import './assets/reset.css'
let isPc = (function() {
    var userAgentInfo = navigator.userAgent;
    var Agents = ["Android", "iPhone",
        "SymbianOS", "Windows Phone",
        "iPad", "iPod"
    ];
    var flag = true;
    for (var v = 0; v < Agents.length; v++) {
        if (userAgentInfo.indexOf(Agents[v]) > 0) {
            flag = false;
            break;
        }
    }
    return flag;
}());
let getDateDiff = function(startDate, endDate) {
    var startTime = new Date(Date.parse(startDate.replace(/-/g, "/"))).getTime();
    var endTime = new Date(Date.parse(endDate.replace(/-/g, "/"))).getTime();
    var dates = Math.abs((startTime - endTime)) / (1000 * 60 * 60 * 24);
    return dates;
}
document.title += getDateDiff((new Date()).getFullYear() + '-' + ((new Date()).getMonth() + 1) + '-' + (new Date()).getDate(), '2017-12-22') + 1 + '天';
export default {
    name: 'app',
    components: {
        StyleEditor,
        ResumeEditor
    },
    data() {
        return {
            interval: 27,
            currentStyle: '',
            enableHtml: false,
            fullStyle: [
                `/*
* 辣辣，嘻嘻嘻！
* 这是我们在一起的第三个情人节咯！
* 这次我没能陪在你身边过情人节，心里一直很愧疚》.《
* 为了补偿我的宝宝
* 先奉上一个情人节纪念礼物
* 你现在用的是 ${isPc ? '电脑' : '手机'}
* 本宝宝猜的准吧
*/

/* 首先给所有元素加上过渡效果 */
* {
  -webkit-transition: all .3s;
  transition: all .3s;
}
/* 白色背景太单调了。来点背景 */
html {
  color: rgb(222,222,222);
  background: rgb(0,43,54); 
}
/* 文字太近了 */
.styleEditor {
  padding: .5em;
  border: 1px solid;
  margin: .5em;
  overflow: auto;
  ${ isPc ? 'width: 48%;height: 96%;' : 'width: 96%;height: 50%;' }
  font-size: 14px;
  line-height:1.5;
}
/* 这些代码颜色都一样。加点儿程序员专用高亮区别来 */
.token.selector{ color: rgb(133,153,0) }
.token.property{ color: rgb(187,137,0) }
.token.punctuation{ color: yellow }
.token.function{ color: rgb(42,161,152) }
.token.comment{ color: rgb(177,177,177) }
/* 平民 3D 效果整一波 */
html{
  -webkit-perspective: 1000px;
          perspective: 1000px;
}
.styleEditor {
  position: fixed; 
  ${ isPc ? 'left: 0;' : 'left:0;right:0;margin:auto;'}
  top: 0; 
  -webkit-transition: none; 
  transition: none;   
  ${ isPc ? '-webkit-transform: rotateY(10deg) translateZ(-100px) ;transform: rotateY(10deg) translateZ(-100px) ;' : '-webkit-transform: rotateX(-10deg) translateZ(-100px) ;transform: rotateX(-10deg) translateZ(-100px) ;' }
  ${ isPc ? '' : '-webkit-transform-origin: 50% 0% 0;transform-origin: 50% 0% 0;' }
}

/* 接下来，掏出我的小本本 */
.resumeEditor{
  position: fixed; 
  ${ isPc ? 'right: 0;' : 'left:0;right:0;margin:auto;'}
  ${ isPc ? 'top: 0;' : 'bottom:2%;'}
  padding: .5em;  
  ${ isPc ? 'margin: .5em;' : ''}
  ${ isPc ? 'width: 48%;height: 96%;' : 'width: 96%;height: 50%;' }
  border: 1px solid;
  color: #222;
  overflow: auto;
  font-size: 14px;
  line-height:1.5;
  ${ isPc ? '-webkit-transform: rotateY(-10deg) translateZ(-100px) ;transform: rotateY(-10deg) translateZ(-100px) ;' : '-webkit-transform: rotateX(10deg) translateZ(-100px) ;transform: rotateX(10deg) translateZ(-100px) ;' }
    ${ isPc ? '' : '-webkit-transform-origin: 50% 0% 0;transform-origin: 50% 0% 0;' }
  }
/* 我开始写了 */


`,
                `
/* 岁月悠长与君语
 * 两年多来的点点滴滴
 * 把他记录在wgqlovewzr这个只属于我们两个的小天地
 */
`,
                `
/* 再加点样式 */
.resumeEditor{
  padding: 2em;
  line-height:1.8;
}
.resumeEditor h2{
  display: inline-block;
  border-bottom: 1px solid;
  margin: 1em 0 .5em;
  font-size:18px;
}
.resumeEditor ul,.resumeEditor ol{
  list-style: none;
}
.resumeEditor ul> li::before{
  content: '•';
  margin-right: .5em;
}
.resumeEditor ol {
  counter-reset: section;
}
.resumeEditor ol li::before {
  counter-increment: section;            
  content: counters(section, ".") " ";  
  margin-right: .5em;
}
.resumeEditor blockquote {
  margin: 1em;
  padding: .5em;
  background: rgba(221,221,221,.5);
}

/* OK。完成！ */

`
            ],
            currentMarkdown: '',
            fullMarkdown: `菜菜 × 辣辣
----

2017年12月22日，那天冬至。硕博公寓，研二楼下，
我鼓足了勇气向你表白
也是那一天，你成为了我的辣辣
不知不觉已经 \`${getDateDiff((new Date()).getFullYear()+'-'+((new Date()).getMonth()+1)+'-'+(new Date()).getDate(),'2016-09-15') + 1}\` 天

在这里我们一起恰过东西
----

* 北京理工大学新食堂
* 北京理工大学七食堂
* 北京理工大学二食堂
* 北京理工大学三食堂
* 北京理工大学清真食堂
* 北京理工大学京工食堂
* 传统饺子馆
* 金榜缘
* 九宫格
* 蜀正园
* 潮汕牛肉火锅
* 肯德基
* 麦当劳
* 必胜客
* 四世同堂
* 德川家
* NOVA
* 金掌勺
* 重庆小面
* 河间驴肉火烧
* 杨国福麻辣烫
* 张亮麻辣烫
* 悠烫
* 左一煎饼
* 102蹄花火锅
* 巫山烤鱼
* 黄焖鸡
* 阿芮烤鸡爪旁边那个韩国料理叫啥来着
* 聚点串吧
* 肉串汪
* 壹食壹客水煎肉
* 醉面
* 星巴克
* 华宇好几层的那个烤肉，好像叫什么时光烤肉
* 锦府盐帮
* 犟牛家榴莲烤肉
* 绿茶餐厅
* 西贝莜面村
* Sizzler西餐厅
* 廖记棒棒鸡
* 犟小面
* 南京大牌档
* 呷哺呷哺
* 好一窝
* 焦耳食堂
* 鳗鳗的爱
* 潮汕砂锅粥（三家不同的店，名字实在记不得了，记得有一家叫十三姨）
* 年糕火锅 打完保龄球，大家一块去吃的
* 还有好多好多，只记得吃了啥，不记得名字的地方，哈哈哈
* ……

一起看过的电影
----

1. 妖猫传
2. 前任3：再见前任
3. 芳华
4. 红海行动
5. 头号玩家
6. 恋爱回旋。
7. 后来的我们
8. 超时空同居
9. 复仇者联盟3
10. 摩天营救
11. 西虹市首富
12. 一出好戏
13. 无双
14. 嗝嗝老师
15. 无敌破坏王
16. 蜘蛛侠：平行宇宙
17. 复仇者联盟4
18. 蜘蛛侠：英雄远征
19. 绝杀慕尼黑
20. 狮子王
21. 哪吒之魔童降世
22. 鼠胆英雄（在家一块看的）
23. 送我上青云（在家一块看的）
24. 受益人
25. 误杀

一起去过的地方
----

* 上海
* 北京
* 天津
* 赤峰
* 齐齐哈尔
* ……

一起玩过的游戏
----

1. 王者荣耀
2. 王者模拟战
3. 五子棋
4. 大家来找茬
5. 欢乐斗地主
6. 你画我猜
7. 俄罗斯方块
8. ……

> 【岁月悠长与君语，往后余生，多多指教】  
> 这回不在你身边，辣辣不要森气，我一定会好好补偿你的啦~
> 从17年我们在一起，到现在，两年多过去了
> 我亲眼见证了辣辣一步一步的变成一个更好的辣辣
> 还记得你快毕业的时候压力大的在我怀里哭
> 还记得你刚刚工作时候一点信心都没有的惆怅
> 现如今
> 你已经是一个独当一面的华为人了
> 辣辣变得越来越优秀，我一直看在眼里，特别的为你高兴
> 辣辣加油~不开心的时候就打开这个网站，回忆我们在一起腻味的时光嘻嘻嘻
> 最后，还是要对你说
> 我爱你，王志茹，你这辈子都是我的了！

`
        }
    },
    created() {
        this.makeResume()
    },

    methods: {
        makeResume: async function() {
            await this.progressivelyShowStyle(0)
            await this.progressivelyShowResume()
            await this.progressivelyShowStyle(1)
            await this.showHtml()
            await this.progressivelyShowStyle(2)
        },
        showHtml: function() {
            return new Promise((resolve, reject) => {
                this.enableHtml = true
                resolve()
            })
        },
        progressivelyShowStyle(n) {
            return new Promise((resolve, reject) => {
                let interval = this.interval
                let showStyle = (async function() {
                    let style = this.fullStyle[n]
                    if (!style) {
                        return
                    }
                    // 计算前 n 个 style 的字符总数
                    let length = this.fullStyle.filter((_, index) => index <= n).map((item) => item.length).reduce((p, c) => p + c, 0)
                    let prefixLength = length - style.length
                    if (this.currentStyle.length < length) {
                        let l = this.currentStyle.length - prefixLength
                        let char = style.substring(l, l + 1) || ' '
                        this.currentStyle += char
                        if (style.substring(l - 1, l) === '\n' && this.$refs.styleEditor) {
                            this.$nextTick(() => {
                                this.$refs.styleEditor.goBottom()
                            })
                        }
                        setTimeout(showStyle, interval)
                    } else {
                        resolve()
                    }
                }).bind(this)
                showStyle()
            })
        },
        progressivelyShowResume() {
            return new Promise((resolve, reject) => {
                let length = this.fullMarkdown.length
                let interval = this.interval
                let showResume = () => {
                    if (this.currentMarkdown.length < length) {
                        this.currentMarkdown = this.fullMarkdown.substring(0, this.currentMarkdown.length + 1)
                        let lastChar = this.currentMarkdown[this.currentMarkdown.length - 1]
                        let prevChar = this.currentMarkdown[this.currentMarkdown.length - 2]
                        if (prevChar === '\n' && this.$refs.resumeEditor) {
                            this.$nextTick(() => this.$refs.resumeEditor.goBottom())
                        }
                        setTimeout(showResume, interval)
                    } else {
                        resolve()
                    }
                }
                showResume()
            })
        }
    }
}
</script>
<style scoped>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

html {
    min-height: 100%;
}
.styleEditor {
    -webkit-backface-visibility: hidden;
}
</style>
