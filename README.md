# Web Workers Demo
Migrate Long Running JS onto a Web Worker

### [Relevant Quiz from Browser Rendering Optimization](https://www.udacity.com/course/viewer#!/c-ud860/l-4138168623/e-4184098558/m-4150829139)

### [Relevant solution from Browser Rendering Optimization](https://www.udacity.com/course/viewer#!/c-ud860/l-4138168623/e-4184098558/m-4146278980)

Working on the quiz? Start by examining index.html and the JavaScript files linked inside it.

#My tips are as follow:
1. 定义Workers文件路径一定要正确，主要你的JS文件是被加载在html文件中，因此应该已html文件的路径来计算。
2. Worker JS文件可以import另外一个JS文件
```importScripts('anotherJS.js');```
3. New一个Work对象时候要用_worker特性检测_:
```if (window.Worker) {
  ...

}```
3. New这个对象成功后才可以调用postMessage([data1,data2])参数实际上是个数组，如果只有一个数据，接受方onMessage(e)通过数组角标来接受，比如e.data[0], e.data[1].
4. 最好接受方的变量定义不同于发送方，不然会出现分不清使用这个变量的时候有可能是发送前的值（全局变量），我就犯过这样的错误。
5. 最好的参考是 [MDN相关文档](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API/Using_web_workers#引入脚本与库)