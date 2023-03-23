# umi3-source-code
Umi3源码学习-1实现运行时
Umi3实战和手写实现运行时

## 1 UMI实现思路
- 1. 启动一个node程序 bin/umi.js -> cli.js
- 2. 启动一个Service 
  - 扫描pages目录，根据它生成临时文件夹里的文件
  - 启动这些临时文件夹里的文件


 一个插件有可能会注册我个钩子，钩子的事件名称肯定是不一样的
{plugin1:[{key:'click',fn},{key:'mouseMove',fn}]}
{plugin2:[{key:'click',fn},{key:'mouseMove',fn}]}
 但是触发的时候是按事件名称来触发的
let hooks = {'click',[fn,fn],mouseMove:[fn,fn]};
 applyPlugin({key:'click'});

 浏览器注册事件的时候
 function on(){
   onclick();
   onmousemove();
   onmouseover();
 }
//devMiddleware
app.use(function(req,res,next){
  读取产出的文件并返回
  let content = fs.readFileSync('./dist/main.js');
res.send(content);
});