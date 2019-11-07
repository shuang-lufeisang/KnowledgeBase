#前言
>**Android开发者应该都有一个痛点，那就是`AndroidStudio`编译慢出翔，一般开始编译，我就可以出去抽个烟了，特别是第一次导入一个工程的时候，下载各种依赖包，如果卡住了，那更加揪心。那么，有没有办法解决？还真有。。只不过比较费钱，市面上有一些私库服务器工具，比较有名的是`Artifactory`，但是费用也不低，好像是一年几万美元...**
>
>**然而，万能的大佬又把他`破解`了. = =!**

搭建一个私库不只是可以`加快编译速度`，还有利于`优化项目管理方式`。
今天的文章，包含 `从0开始`，搭建一个`私库`，上传`本地`依赖包，添加`远程`代理等一系列 干货内容。
OK，踩油门，松离合，出发！


#正文大纲
 >**一、破解
 >二、启动服务
 >三、上传本地库
 >四、添加远程代理
 >五、将私库应用到`AndroidStudio`工程中**

#正文
##一、破解
既然是正版软件的破解，那当然是先拿到破解包（`神马？你问我破解包去哪里下载？度娘咯，谷歌咯，实在找不到就问我要咯`···`百度网盘`）：
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-c877253fd0e09d96.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>它是一个zip包，解压之后里面是：![image.png](https://upload-images.jianshu.io/upload_images/4100513-b9b0b43cd1314657.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>继续解压 免安装包zip。![image.png](https://upload-images.jianshu.io/upload_images/4100513-cde8189e7a6fd22c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>OK.可以开始破解了：
>运行cmd：![image.png](https://upload-images.jianshu.io/upload_images/4100513-ae25e65ba577ed9d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>我们选2：![image.png](https://upload-images.jianshu.io/upload_images/4100513-58445a726de4a12b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>home目录，就是 我们刚才解压免安装包之后的那个目录：`C:\WorkRoot\Artifactory\artifactory_pro_and_crack\artifactory-pro-6.6.0`
>输入进去，回车：![image.png](https://upload-images.jianshu.io/upload_images/4100513-1c6aff84a4fa1fa6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>然后就开始破解。最后完成破解的样子是：![image.png](https://upload-images.jianshu.io/upload_images/4100513-3e31aa1b16eda69d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>再下一步，生成license，这是 破解软件帮我们生成的一个 证书，等会用得着，先拷贝出来 放着。![image.png](https://upload-images.jianshu.io/upload_images/4100513-2de43058d03d332e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

欧了，破解完成。

***
##二、启动服务

`artifactory.bat`右键 - 以管理员身份运行
![image.png](https://upload-images.jianshu.io/upload_images/4100513-9899ad682c85f8b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>然后你能看到这个：![image.png](https://upload-images.jianshu.io/upload_images/4100513-72a5e7ffc5a6b313.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>那你就可以起浏览器输入： `http://127.0.0.1:8081` 回车：你就会看到这个：
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-4d3b94071fb39657.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


还记得我们之前拷贝的`license`么？
点这里的`next`，然后粘贴进去，
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-b583d55f059fb1b9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>注: 这里可能会卡住，一直在转圈。。。如果你不幸遇到了，那就从第一步开始重新来吧。

然后一路`next`或者`skip`，就完事了。大功告成！
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-d1b0f096d91283da.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##三、上传本地库
>我们平时会开发自己的`library`，如果项目管理比较专业的话，应该会上传到公司内部的私有库里面去，然后在项目开发时，大家使用相同的内部仓库依赖包，达成协调统一。
>那么，如何上传自己的`library`呢？很简单。

两步走：
1、建立自己的`local`仓库
>![](https://upload-images.jianshu.io/upload_images/4100513-44bc3e2d899a0b9b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>![](https://upload-images.jianshu.io/upload_images/4100513-a735589ee3dc80ec.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>这样，仓库就建好了

2、向仓库中去上传文件
>![](https://upload-images.jianshu.io/upload_images/4100513-f8f642a9333cf16e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![](https://upload-images.jianshu.io/upload_images/4100513-a2d7bbb893ec5b24.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

我上传一个` aar `包 试试：
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-eb49aa45b3bfd1ae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![上传成功](https://upload-images.jianshu.io/upload_images/4100513-27a556eb39e6ff3a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>然后我们就看到了刚刚上传的aar

这里有个细节：如果你的文件比较大，超过比如超过100M，就会被告知无法上传，那么这个100M的限制在哪里呢？
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-ad8e256062e5aece.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![image.png](https://upload-images.jianshu.io/upload_images/4100513-5ef64d70f8d75e15.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***

##四、添加远程代理
>私有库整完了，那么如果是挂在国外的依赖库，有时候网络很慢甚至被墙，那么搭建新的开发环境就很糟心了。也有办法解决，用公司内部的私库代理远程的  google jcenter 等，只需要下载一次，就会存到私库上，下一次如果有新同事要搭建环境，就会直接使用私库上的依赖包，节省很多时间。

>![](https://upload-images.jianshu.io/upload_images/4100513-d448afed69ca0c34.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![](https://upload-images.jianshu.io/upload_images/4100513-3b8e97e27bd715ee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![image.png](https://upload-images.jianshu.io/upload_images/4100513-563c097587358f48.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![](https://upload-images.jianshu.io/upload_images/4100513-4f11b22bc5777976.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>点`保存`，然后你就会看到我们刚刚创建的远程代理：
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-47c07a9a2b2cbfb3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

可能有人会问，我们要代理远程url，那么这个远程url从哪里来呢？
>答：从源码里面来，不过不是sdk源码，而是gradle源码：![](https://upload-images.jianshu.io/upload_images/4100513-dadc8c1591e013d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>像这么一个项目：`androidStudio`默认就会给你2个仓库地址，一个google，一个jcenter，我们可以ctrl点进去，然后找到：
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-51f332f981174dfe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![image.png](https://upload-images.jianshu.io/upload_images/4100513-14dfacb96b37eadd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>另外，你也可以使用阿里云的代理地址（`https://maven.aliyun.com/mvn/view`），大厂总是有办法绕过防火墙。
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-c7155823a4d77c38.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
***
##五、将私库应用到AndroidStudio工程中
上面搭建了私库，那么这些东西应该怎么用到我们的项目里面？
默认情况下，本地私库仓库的地址都是 `http://localhost:8081/artifactory/`,我们只需要在它的后面接上`我们自己的 local库或者remote库的名字`就行了。就像下面这样：
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-0d507d590bceb9c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>完了，就这么简单。
>但是这里有个细节。有时候我们会用到多个`remote`代理，时间一长，`gradle`里面也会显得很乱，为了让`gradle`更加简洁，我们可以使用`artifactory`的虚拟分组：
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-1b7ffe33f872be32.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-d5f841997d9a6857.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-6ed015b4efca4a99.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>点保存，然后我们就能看到我们的虚拟分组了。
>![image.png](https://upload-images.jianshu.io/upload_images/4100513-f2c3f1e382f96b57.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#结语
>懂点后台的朋友都知道，其实这个artifactory原理就是 Tomcat+项目部署的方式，实现私库。
>有些做SDK的厂家，会把自己的SDK包放在 公网artifactory上，然后让 开发者去 引用他们的artifactory库。
>不过这些我们个人开发者或者中小型团队暂时用不着。
>如果artifactory破解包实在找不到，请留言联系本人。