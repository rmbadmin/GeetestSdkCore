# Gt C# SDK [![NuGet](https://img.shields.io/nuget/v/GeetestSdkCore.svg?label=nuget&style=flat-square)](https://www.nuget.org/packages/GeetestSdkCore/)

支持.Net Framework4.6 && .NET Core 1.0及以上版本．本项目提供的Demo的前端实现方法均是面向PC端的。 本项目是面向服务器端的，具体使用可以参考[文档](http://www.geetest.com/install/sections/idx-server-sdk.html), 客户端相关开发请参考我们的[前端文档](http://www.geetest.com/install/)。

**注意事项：部署在生产环境中时，需要将gt.js文件存放到项目中并在页面中引用该文件。该js的作用是充分利用多CDN，使静态文件尽可能加载成功。**

# 开发环境
```
    Visual Studio 2017
    .NET Standard 1.3
```
# 快速开始

1. 从 Nuget 引用包
```
PM Install-Package GeetestSdkCore
```
2. 根据你的.Net Framework版本编译代码(或者用VS打开项目直接运行DEMO)．
3. 将编译完成的DLL引入你的项目.
4. 编写你的代码，代码示例:

```
	using System;
	using System.Collections.Generic;
	using System.Linq;
	using System.Web;
	using System.Web.UI;
	using System.Web.UI.WebControls;
	using GeetestSDK;

	namespace demo
	{
	    public partial class GetCaptcha : System.Web.UI.Page
	    {
	        protected void Page_Load(object sender, EventArgs e)
	        {
	            Response.ContentType = "application/json";
	            Response.Write(getCaptcha());
	            Response.End();
	        }
	        private String getCaptcha()
	        {
	            GeetestLib geetest = new GeetestLib(GeetestConfig.publicKey, GeetestConfig.privateKey);
	            Byte gtServerStatus = geetest.preProcess();
	            Session[GeetestLib.gtServerStatusSessionKey] = gtServerStatus;
	            return geetest.getResponseStr();
	        }
	    }
	}
```
# 发布日志

+ 3.1.1

  统一接口

+ 3.1.0

  添加challenge加密特性，使验证更安全， 老版本更新请先联系管理员

+ 2.0.2

    修复Failback Bug

+ 2.0.1 

     完善注释
     添加API文档
     修改Demo
+ 2.0.0

     去除旧的接口
     添加注释
