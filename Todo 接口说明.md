### 接口详细
## 一：获取 Todo List 数据  
**请求类型：** post  
**请求Url：** http://127.0.0.1:8888/gettodolist  
**接口描述：**

## 请求参数列表：  
|变量名  |类型   |含义  |备注|
|-------|-------|-----|----|
|name   |String |用户名|&nbsp;|
## 响应参数列表：  
|变量名  |类型   |含义  |备注|
|:-------|-------|-----|----|
|—resData|object|  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;—user|object|用户信息对象  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name  |string  |用户名  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;id  |string  |用户ID  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;—list  |array&lt;object&gt;  |  todo 对象数组|  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;id  |string  |该 todo 的ID  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;createtime  |string  |创建时间  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;content  |string  |内容  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;started  |boolean  |？  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;finished  |boolean  |是否完成  |  &nbsp;|


**实例：**
```
$(".btn").on("click",function(){

    url = "http://127.0.0.1:8888/gettodolist";
    $.post(url,  {name:'frank'},  function(data) {
        console.log(data);
    });
    
})
```

## 二：存储 Todo List 数据  
**请求类型：** post  
**请求Url：** http://127.0.0.1:8888/addtodolist  
**接口描述：**

## 请求参数列表：  
|变量名  |类型   |含义  |备注|
|-------|-------|-----|----|
|name   |String  |用户名  |  |
|resData|string  |要保存的 相关数据  |此对象既是上面表格的所有内容,但**是string类型的**。一定要把之前的(如果有) todolist 和新的 todolist 加在一起，因为**此接口只会覆盖数据，不会追加！！！**|

**实例：**
```
const data = 
`{  //注意" `` "这个符号，表示这里面的内容是字符串类型的，并且支持跨行！！！
    "user":{
        "name":"frank",
        "id":"123"
    },
    "list":[
        {
            "id":"2016091602",
            "createtime":"2016-09-16",
            "content":"夜晚煮面记得打两个鸡蛋，小心油溅到身上哦",
            "started":true,
            "finished":false
        },{
            "id":"2016091682",
            "createtime":"2016-09-16",
            "content":"天气阴晴不定，一定要随身带把伞哦",
            "started":false,
            "finished":true
        }
    ]
}`;

$(".btn").on("click",function(){
    var map = {
        name :'frank',
        resData:data,
    };
    url = "http://127.0.0.1:8888/addtodolist",
    $.post(url, map , function(data) {
        console.log(data);
    });
})
```