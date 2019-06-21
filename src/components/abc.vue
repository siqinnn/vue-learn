<template>
  <div id="hello">
    {{message}}
    <h1>{{ msg }}</h1>
    <!-- <p id="kk">当前时间：{{time}}</p> -->

    <button v-on:click="counter += 1">Add 1</button>
    <button v-on:click="counter -= 1">jian 1</button>
    <p>执行加一与减一操作 {{ counter }} times.</p>

    <button @click="show">click</button>
    <button @mouseover="show">mouseover</button>
    <button @mouseout="show">mouseout</button>
    <button @mouseenter="show">mouseenter</button>
    <button @mouseleave="show">mouseleave</button>
    <button @mousedown="show">mousedown</button>
    <button @mouseup="show">mouseup</button>
    <button @mousemove="show">mousemove</button>
    <button @dblclick="show">dblclick</button>
    <button @click="dian">点击</button>

    <input type="text" id="p1">
    <input type="text" id="p2">
    <button @click="jiaa()">运算</button>
    <button @click="day()">周几</button>
    <input type="text" value id="jiao">
    <button @click="daform()">提交</button>
    <button @click="ann()" id="niu">按呀</button>
    <button @click="pinjie()">按钮1</button>
    <button @click="han()">按钮2</button>
    <div id="hezi"></div>
    <span id="zhangsan">张三:</span>
    <input type="text" id="biaodan">
    <button id="anya" @click="haha()" name>haha</button>

    <button @click="las()">方法</button>

    <div class="toFlex">
      <div>
        <!-- vue动态切换class样式 -->
        <!-- 使用三目判断 ，useIt为自定义的class样式-->
        <h4 id="demo" :class="useItrr?'useIt':''">改变颜色</h4>
        <button @click="bian">变颜色</button>
      </div>
      <div>
        <!-- DOM操作 -->
        <p id="kk" v-html="inner"></p>
        <button @click="display()" class="oo">显示时间</button>
      </div>
      <div>
        <input id="kuang" type="text">
        <!-- <button @click="panduan($event)">判断</button> 不传参，不用加小括号 -->
        <button @click="panduan">判断</button>
      </div>
      <div>
        <button @click="change()">亮与灭</button>
        <img id="im" :src="Imgstr">
      </div>
      <div>
        <ul id="isUl">
          <li class="isSS" v-for="ss of liArr" :key="ss">{{ss}}</li>
        </ul>
      </div>
      <div>
        <div :class="{'actived':hActived}" @click="changecolor">点击我改变颜色</div>
        <ul id="ul">
          <li
            v-for="(list,index) in datas"
            :key="index"
            @click="xuanka(index)"
            :class="{'bor':clicked==index}"
          >{{list}}</li>
        </ul>
        <button class="gaga" @click="heihei">es6按钮1</button>
        <button class="gaga" @click="heihei1">es6按钮2</button>
        <button class="gaga" @click="heihei2">es6按钮3</button>
        <button class="gaga" @click="heihei3">es6按钮4</button>
        <button class="gaga" @click="heihei4">es6按钮5</button>
        <button class="gaga" @click="heihei5">es6按钮6</button>
        <button class="gaga" @click="heihei6">es6按钮7</button>
        <div>
          <button class="gaga" @click="heihei7">vue按钮8</button>
          <p :style="{background:color}">{{color}}</p>
        </div>
        <button class="gaga" @click="heihei8">es6按钮9</button>
        <button class="gaga" @click="heihei9">es6按钮10</button>
        <button class="gaga" @click="heihei10">es6按钮11</button>
      </div>
    </div>
  </div>
</template>

<script>
import { setInterval } from "timers";
export default {
  //    el: '#hello',
  props: {
    msg: String
  },

  data() {
    return {
      message: "比财数据科技",
      counter: 0,
      time: Date(),
      inner: "",
      useItrr: false, // 动态切换class样式用
      Imgstr: "", // 存储图片src
      liArr: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      hActived: false,
      datas: ["选项1", "选项2", "选项3", "选项4", "选项5"],
      clicked: 0,
      color: ""
    };
  },
  // 页面加载前执行，完全与标签无关的数据操作
  created() {},
  // 监听页面里任何的操作，只要页面（以标签为参考）发生变动，就执行
  mounted() {
    this.ann();
  },
  methods: {
    //改变颜色
    bian() {
      //   var q = document.getElementById("demo");
      //   q.style.color = "#ff0000";
      this.useItrr = !this.useItrr;
    },
    //获取当前时间
    display() {
      // vue及es6 里的方法，推荐用，但很少用
      let inner = `<p>innerhtml内容：${Date()}</p>`;
      this.inner = inner;
      // es5 里的方法，不推荐用
      //   document.getElementById("kk").innerHTML = ;
    },
    //判断是否是数字
    panduan() {
      var j = document.getElementById("kuang").value;
      //   if (j == "" || isNaN(j)) {
      //     alert("不是数字");
      //   }
      let num1 = "222";
      let num2 = j;
      let num3 = 222;
      console.log(typeof +num1); // 一般用于转换遇到内容为数字的字符串：'222'，
      console.log(typeof ("" + num3)); // 一般用于遇到内容不确定类型时，转换成字符串：222，
      console.log(typeof num2);

      //   if (typeof num === "number") {
      //     console.log("数字");
      //   } else {
      //     console.log('不是数字');
      //   }
    },

    //切换图片
    change() {
      this.useItrr = !this.useItrr;
      this.useItrr
        ? (this.Imgstr = require("../assets/3.gif"))
        : (this.Imgstr = require("../assets/4.gif"));
      console.log(this.Imgstr);
      //   var d = document.getElementById("im");
      //   d.src = d.src.match("bulboff")
      //     ? "assets/pic_bulbon.gif"
      //     : "assets/pic_bulboff.gif";
    },

    //事件触发
    show() {
      console.log("触发");
    },

    //弹框
    dian() {
      window.alert("点击了我");
    },

    //加法运算
    jiaa() {
      var p1 = document.getElementById("p1").value;
      var p2 = document.getElementById("p2").value;
      var p3 = parseInt(p1) + parseInt(p2);
      alert(p3);
    },
    day() {
      //case语句获取日期
      var cc;
      var ccc = new Date().getDay();
      switch (ccc) {
        case 0:
          alert((cc = "今天是星期日"));
          break;
        case 1: // 一般这样写
          cc = "今天是星期一";
          alert(cc);
          break;
        case 2:
          alert((cc = "今天是星期二"));
          break;
        case 3:
          cc = "今天是星期三";
          alert(cc);
          break;
        case 4:
          alert((cc = "今天是星期四"));
          break;
        case 5:
          alert((cc = "今天是星期五"));
          break;
        case 6:
          alert((cc = "今天是星期六"));
          break;
      }
    },
    //表单验证 其它方法
    daform() {
      var pi = document.getElementById("jiao").value;
      if (pi == null || pi == "") {
        alert("请输入姓名");
        return false;
      } else {
        window.open("https://www.baidu.com");
      }
    },
    //时间监听
    ann() {
      document.getElementById("niu").addEventListener("click", function() {
        alert("helloword");
      });
    },
    //数组合并
    pinjie() {
      var zx = [1, 2, 3];
      document.write(zx.concat(4, 5, 6));
      //   .split(); // 分割字符串
      //   arrary.slice(); // 从已有的数组中返回选定的元素。
      //   arrary.join(); // 把数组中的所有元素放入一个字符串。
      //   arrary.push(); // 向数组的末尾添加一个或多个元素，并返回新的长度。
      //   arrary.unshift(); // 向数组头部添加
      //   arrary.shift(); //数组的第一个元素从其中删除，并返回第一个元素的值。
      //   arrary.pop(); // 删除并返回数组的最后一个元素。
      //   arrary.indexOf("kk") > -1; // 判断kk是否在数组内，存在既大于-1
      //返回某个指定的字符串值在字符串中首次出现的位置。

      //   arrary.substring();用于提取字符串中介于两个指定下标之间的字符。
      //   arrary.substr();在字符串中抽取从 start 下标开始的指定数目的字符。
    },

    //数组合并
    han() {
      var big = ["tom", "jack", "katrina"];
      var small = ["haha", "hehe", "lala"];
      var bigg = ["sha", "ben"];
      var para = big.concat(small, bigg);
      document.write(para); // 不常用，他会清除已有的页面内容
    },
    //聊天窗口
    haha() {
      //   console.log(self);
      //   var q1 = document.getElementById("hezi");
      //   var q2 = document.getElementById("biaodan");
      //   var q3 = document.getElementById("zhangsan");
      //   //   var q4 = document.getElementById("anya")
      //   q1.innerHTML = q1.innerHTML + "张三:" + q2.value + "</br>";
      //   q3.value = "";
      //   //
      let a1 = document.getElementById("isUl");
      let a2 = document.getElementsByClassName("isSS");
      let a3 = document.getElementsByTagName("li");
      let a4 = document.querySelector("li");
      let a5 = document.querySelectorAll(".isSS");
      console.log("a1", a1);
      console.log("a2", a2);
      console.log("a3", a3);
      console.log("a4", a4);
      console.log("a5", a5);
    },
    // las(){
    //      // let st="what are you doing ?"
    //      let st="what：are：you：doing：?"
    //      console.log(st.split("",3))
    // },
    // las() {
    //   var arr = new Array(6);
    //   arr[0] = "tom";
    //   arr[1] = "jerry";
    //   arr[2] = "jack";
    //   arr[3] = "alin";
    //   arr[4] = "angela";
    //   arr[5] = "tomas";
    //   console.log(arr.splice(2,4))
    // }
    // las() {
    //   var arr = new Array(6);
    //   arr[0] = "tom";
    //   arr[1] = "jerry";
    //   arr[2] = "jack";
    //   arr[3] = "alin";
    //   arr[4] = "angela";
    //   arr[5] = "tomas";
    //   console.log(arr.join("@"));
    //   console.log(arr.join("      "));
    // }
    // las() {
    //   var arr = new Array(6);
    //   arr[0] = "tom";
    //   arr[1] = "jerry";
    //   arr[2] = "jack";
    //   arr[3] = "alin";
    //   arr[4] = "angela";
    //   arr[5] = "tomas";
    //   console.log(arr.push("siqin"));

    // }
    // las() {
    //   var arr = new Array(6);
    //   arr[0] = "tom";
    //   arr[1] = "jerry";
    //   arr[2] = "jack";
    //   arr[3] = "alin";
    //   arr[4] = "angela";
    //   arr[5] = "tomas";
    //   console.log(arr.unshift("siqin"));

    // }
    //  las() {
    //   var arr = new Array(6);
    //   arr[0] = "tom";
    //   arr[1] = "jerry";
    //   arr[2] = "jack";
    //   arr[3] = "alin";
    //   arr[4] = "angela";
    //   arr[5] = "tomas";
    //   console.log(arr.shift("tomas"));

    // }
    // las() {
    //   var arr = new Array(6);
    //   arr[0] = "tom";
    //   arr[1] = "jerry";
    //   arr[2] = "jack";
    //   arr[3] = "alin";
    //   arr[4] = "angela";
    //   arr[5] = "tomas";
    //   console.log(arr.pop("tomas"));

    // }
    las() {
      let st = "what are you doing ?";
      console.log(st.substring(3));
      console.log(st.substring(3, 6));
    },
    changecolor() {
      this.hActived = !this.hActived;
    },
    xuanka(index) {
      this.clicked = index;
    },
    heihei() {
      function one(x, y) {
        //es6允许为函数的参数设置默认值，直接写在定义参数的后面
        if (typeof y == undefined) {
          //判断下y有没有被赋值，如果没有，再等于默认值
          y = "world";
        }
        y = y || "world";
        console.log(x, y);
      }
      one("hello");
      one("hello", "china");
      one("hello", "");
    },
    heihei1() {
      function po(x = 0, y = 0) {
        this.x = x;
        this.y = y;
      }
      const pp = new po();
      pp;
      console.log(pp);
    },
    heihei2() {
      let x = 99;
      function foo(p = x + 1) {
        console.log(p);
      }
      foo();
      x = 100;
      foo();
    },
    heihei3() {
      let foo = "outer";
      function bar(func = () => foo) {
        // let foo='inner';
        console.log(func());
      }
      bar();
    },
    heihei4() {
      function push(array, ...items) {
        array.push(...items);
      }
      function add(x, y) {
        return x + y;
      }
      const number = [4, 38];
      add(...number);
      console.log(add(...number));
      //...是扩展运算符。该运算符将一个数组，变为参数序列。
    },
    heihei5() {
      //复制数组
      const q1 = [1, 2, 3];
      const q2 = q1;
      q2[0] = 2;
      console.log(q1);
    },
    heihei6() {
      //克隆
      const a1 = [1, 2];
      const a2 = [...a1];
      console.log(a2);
    },
    heihei7() {
      //随机获取颜色
      let num1 = Math.random() * 255;
      let num2 = Math.random() * 255;
      let num3 = Math.random() * 255;
      let str = `rgba(${num1},${num2},${num3},0.3)`;
      this.color = str;
      console.log(Math.random());
    },
    heihei8() {
      //用...合并数组
      const st1 = ["a", "b", "c"];
      const st2 = ["d", "e"];
      console.log([...st1, ...st2]);
    },
    heihei9() {
      //super关键字  指向档期按对象的原型对象

      //set 类似数组，  成员值都是唯一的   可以数组去重
      const s = new Set();
      [2, 3, 4, 5, 2, 2].forEach(x => s.add(x));
      for (let i of s) {
        console.log(i);
      }
    },
    heihei10() {
      const set = new Set([1, 1, 2, 2, 3, 3, 3, 4, 4, 4, 5]);
      console.log([...set]);
    },
    heihei11() {}
  }
};
</script>
f
<style scoped >
h1 {
  color: red;
}
button {
  width: 60px;
  height: 30px;
  background: gray;
}
.aa {
  width: 180px;
  height: 30px;
  margin: 0 auto;
}
.oo {
  width: 150px;
}
#hezi {
  width: 200px;
  height: 300px;
  background: hotpink;
}

/* 弹性盒子 */
.toFlex {
  display: flex;
  justify-content: space-between;
}
.useIt {
  font-weight: bold;
  color: red;
}
.isSS {
  color: red;
}
.actived {
  color: hotpink;
}
#ul li {
  margin-left: 3px;
  list-style: none;
  float: left;
  width: 50px;
  height: 20px;
  background: salmon;
}
.bor {
  border: 3px solid black;
}
.gaga {
  width: 100px;
  height: 30px;
  background: green;
}
</style>
