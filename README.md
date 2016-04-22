#jquery-edittable－treetable
####基于boostrap和jquery的可编辑树表插件
#项目依赖
####jquery boostrap
#为什么要做这个插件
传统的树表在进行批量增删改查时需要点击多次，操作流畅度和易用性很不好，于是开发了这个基于批量表格编辑插件，比较适用于批量商品分类维护、组织、部门维护等功能。

话不多说 直接点下面的demo看看效果吧
####[项目地址](https://github.com/songhlc/jquery.edittreetable)

####[demo地址](https://github.com/songhlc/bootstrap-treeselect/tree/master/examples/example.html)

###使用方式(单字段维护)

* data:树形数据
* maintitle:字段名称
* nodeupdateCallback:function(data,callback):节点更新回调函数
* nodeaddCallback(data,callback):节点添加回调函数(添加的数据,回调函数)
* noderemoveCallback(data,callback):节点删除回调函数

###code

    $("#bs-treeetable").bstreetable({
        data:data,
        maintitle:"公司名称",
	    nodeaddCallback:function(data,callback){
	        //do your things then callback 新增的时候会返回一个字段叫pinnercode,表示父节点的innercode
	        callback({id:18,name:data.name,innercode:"ttttt",pid:data.pid});
        },
        noderemoveCallback:function(data,callback){
	        //do your things then callback
	        callback();
        },
        nodeupdateCallback:function(data,callback){
	        //do your things then callback
	        callback();
        }
    });


###对应data数据格式(data format)
注意按照pid升序排序(data order by pid asc)

    var data = [
		{name:"test",id:1,pid:0,innercode:1},
		{name:"test",id:12,pid:0,innercode:12},
		{name:"test",id:13,pid:0,innercode:12},
		{name:"test",id:14,pid:0,innercode:12},
		{name:"test",id:15,pid:0,innercode:12},
		{name:"test",id:16,pid:0,innercode:12},
		{name:"test",id:17,pid:0,innercode:12},
		{name:"test",id:18,pid:0,innercode:12},
		{name:"test",id:19,pid:0,innercode:12},
		{name:"test",id:20,pid:0,innercode:12},
		{name:"test",id:21,pid:0,innercode:12},
		{name:"test2",id:2,pid:0,innercode:2},
		{name:"test3",id:3,pid:0,innercode:3},
		{name:"test4",id:4,pid:1,innercode:4},
		{name:"test5",id:5,pid:1,innercode:5},
		{name:"test6",id:6,pid:4,innercode:6},
		{name:"test7",id:7,pid:4,innercode:7},
		{name:"test8",id:8,pid:4,innercode:8},
		{name:"test9",id:9,pid:4,innercode:9},
		{name:"test10",id:10,pid:6,innercode:10},
		{name:"test11",id:11,pid:7,innercode:11},
    ];

###多字段维护
配置中添加参数

- title:列名
- type:input表示输入框(目前只支持简单输入框)
- key:对应数据中的字段


     extfield:[		      
         {
            title:"innercode",
            key:"innercode",
            type:"input"
         }
     ]


