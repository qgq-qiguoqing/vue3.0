vue3.0初体验

## **压缩包体积更小**

当前最小化并被压缩的 Vue 运行时大小约为 20kB（2.6.10 版为 22.8kB）。Vue 3.0捆绑包的大小大约会减少一半，即只有10kB！

## ** Proxy 替换Object.defineProperty **

Object.defineProperty是一个相对比较昂贵的操作，因为它直接操作对象的属性，颗粒度比较小。将它替换为es6的Proxy，在目标对象之上架了一层拦截，代理的是对象而不是对象的属性。这样可以将原本对对象属性的操作变为对整个对象的操作，颗粒度变大。

javascript引擎在解析的时候希望对象的结构越稳定越好，如果对象一直在变，可优化性降低，proxy不需要对原始对象做太多操作。

## **Virtual DOM 重构**

vdom的本质是一个抽象层，用javascript描述界面渲染成什么样子。react用jsx，没办法检测出可以优化的动态代码，所以做时间分片，vue中足够快的话可以不用时间分片。

虽然 Vue 能够保证触发更新的组件最小化，但在单个组件内部依然需要遍历该组件的整个 vdom 树。

传统 vdom 的性能跟模版大小正相关，跟动态节点的数量无关。在一些组件整个模版内只有少量动态节点的情况下，这些遍历都是性能的浪费。

JSX 和手写的 render function 是完全动态的，过度的灵活性导致运行时可以用于优化的信息不足

虽然vue2.0.X也支持ts，相对于vue3.0

3.0修改了组件的声明方式，改成了类式的写法，这样使得和TypeScript的结合变得很容易。

此外，vue的源码也改用了TypeScript来写。其实当代码的功能复杂之后，必须有一个静态类型系统来做一些辅助管理，如React使用的Flow，Angular使用的TypeScript。现在vue3.0也全面改用TypeScript来重写了，更是使得对外暴露的api更容易结合TypeScript。

### **接下来安装体验一下吧**

第一步，安装 vue-cli：

```
npm install -g @vue/cli
```

如果电脑安装过可能会报错 因为安装的是最新的vue-cli 。我安装的是Vue CLI v4.4.4，出现报错，按照提示找到目录文件 。删除有关vue的所以文件重新安装即可

第二步，初始化 vue 项目：

```
vue create vue-next-test
```

输入命令后会出现交互窗口

![1592366966914](C:\Users\qiguoqing\AppData\Roaming\Typora\typora-user-images\1592366966914.png)

有两种创建方式选择

第一种default (babel, eslint) 直接创建 不用选择配置什么的 傻瓜式创建

我个人比较喜欢第二种方式 Manually select features  选中后会出现以下 根据情况自己选择安装

![1592367192097](C:\Users\qiguoqing\AppData\Roaming\Typora\typora-user-images\1592367192097.png)

选择css扩展语言

![1592367268044](C:\Users\qiguoqing\AppData\Roaming\Typora\typora-user-images\1592367268044.png)

选择代码规范检测

![1592367332204](C:\Users\qiguoqing\AppData\Roaming\Typora\typora-user-images\1592367332204.png)

选择 avaScript测试框架  看个人习惯用那个吧

![1592367478998](C:\Users\qiguoqing\AppData\Roaming\Typora\typora-user-images\1592367478998.png)

选中往下点就好了

最后运行 看一下vue3.0d 源码 体验一下吧

最后提醒一下vue3.0的运行命令是：npm run serve

放上vue-cli版本 https://github.com/vuejs/vue-cli/blob/dev/CHANGELOG.md