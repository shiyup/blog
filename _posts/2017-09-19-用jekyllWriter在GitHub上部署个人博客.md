---
title: 用jekyllWriter在GitHub上部署个人博客
layout: post
---
<u>GitHub是什么？</u>

GitHub是一个利用Git进行版本控制、专门用于存放软件代码与内容的共享虚拟主机服务（来自维基百科），我更愿意把它称作程序员的社交网站。GitHub的中心是代码，程序员们加入到不同的项目中，围绕着代码进行相互交流。

<u>GitHub Pages是什么？</u>

GitHub Pages最早是为托管在GitHub上的项目提供介绍页面而诞生的，开发者们可以通过GitHub Pages为他们的每一个项目创建一个用于介绍该项目的静态网站。

<u>Jekyll是什么？</u>

后来有人利用GitHub Pages建立了个人博客，但是由于GitHub Pages的网站是静态的，每次更新博客都需要手动更改HTML、接着GitHub联合创始人Tom Preston-Werner利用Ruby编写了静态网站生成工具Jekyll。Jekyll可以根据提供的模板以及文章内容自动生成静态网站，它的出现将网站的外观（模板）与网站的内容（博文）分开，简化的静态网站的维护。GitHub Pages也部署了Jekyll，上传到GitHub Pages的模板和博文可以被自动地通过Jekyll生成为一个静态网站。

<u>利用Jekyll Writer在GitHub部署Jekyll网站</u>

Jekyll Writer是一款可视化的Jekyll网站管理程序，使用它可以避免接触Git和Jekyll来部署和管理Jekyll网站。
对于从没有接触过GitHub的用户，需要先到GitHub网站上注册一个用户，注册的过程我就不详细讲了。
登录GitHub之后，点右上角的头像选择setting，选择左边栏最后一个personal access tokens，再点击右上角的“Generate new token”生成一个token，Token description填写Jekyll Writer，Select scopes勾选repo。
生成完毕之后记录下这个token准备后面使用。
[下载jekyll Writer](http://www.jekyllwriter.com)运行Jekyll Writer，选择Account标签，点击GitHub，在弹出的窗口中点击Add Account，将生成的Token填入文本框中，最后点击OK。如果一切顺利，就可以看到询问是否要立即扫描该账户下Jekyll仓库的提示了，点击OK继续。

扫描结束后，点击账户名就可以看到所有被搜索到的Jekyll网站了，如果没有，列表就是空的。点击下面的Create new site来创建一个新的Jekyll网站。

如果这是你的第一个网站，那么路径后面可以空着什么都不写，否则填写一个合适的路径。
然后点击后面的对号确认创建，稍等片刻后提示创建成功。
这样一个Jekyll网站就创建完毕了。网站创建完毕后的URL是http://github.io/，比如我在GitHub的用户名是shiyup，我刚刚创建的网站路径是blog，那么这个网站的访问地址就是http://shiyup.github.io/blog。

网站创建成功之后，在Account标签下Blog Account区域的下拉菜单中就可以看到刚刚创建的网站，并切换到该网站。

点击左上角File按钮，选择菜单中的Open Post List菜单，在弹出的窗口中点击右上角的同步按钮进行同步。

同步完成后即可看到完整文章列表了。点击列表中的文章标题即可对文章进行修改

当然，在GitHub上写博客还有一个好处，就是可以利用Git版本控制这一特性管理博文历史。如果你对Git并不熟悉也无需担心，Jekyll Writer已经提供了使用方便的版本管理功能。打开任意一篇文章，切换到Account标签，点击History即可看到这篇文章的所有历史记录，点击历史记录即可打开相应的文章。

<u>管理Jekyll网站</u>

Jekyll Writer不仅可以对文章进行管理，同时对网站也可以进行管理，包括网站参数设置、域名绑定已经更改主题等等。

Jekyll Writer提供了一个在线的主题市场，点击Account标签下的Theme即可看到主题市场中的所有主题，点击Preview可以看到主题的应用效果，点击Apply会自动替换该主题。

不过现在主题市场中的主题还有点少，大家遇到好看的主题也可以向Jekyll Writer Theme投稿，但所投稿的主题要求一定是开源的。

点击Config对网站设置进行更改，多数情况下除了网站标题外等大部分的设置无需更改，具体参数可以参考Jekyll官方网站的[文档](http://jekyll.com.cn/)。

__绑定域名__只需点击Domain后填写完整域名，然后点击Update即可。在Jekyll Writer设置完域名之后，对于二级域名，需要登录域名的DNS后台，添加一条CNAME记录指向你的网站.http://github.io。但如果你要直接绑定裸域，假如你的域名是http://awesome.com，同时希望http://awesome.com和http://www.awesome.com都能访问到你的博客，那么在Jekyll Writer中你应将域名设置为http://awesome.com，同时在http://awesome.com的DNS后台添加两条主机名为@的A记录分别指向192.30.252.153和192.30.252.154，再添加一条主机名为www的CNAME记录指向裸域http://awesome.com。