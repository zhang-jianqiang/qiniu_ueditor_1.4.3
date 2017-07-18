Ueditor七牛云存储版本
===========

>注意事项 老版本请查看 : [https://github.com/widuu/qiniu_ueditor_1.4.3/tree/v1.0.0](https://github.com/widuu/qiniu_ueditor_1.4.3/tree/v1.0.0)
目前使用时发现有问题，会提示后台配置错误，上传插件无法使用

### 新版本说明

>注意：新版本不兼容老版本，网上整合教程现在最多的是老版本，如果查看的是网站教程请点击老版本地址来下载老版本

#### 新增

 - 采用Ueditor官方最新版本【1.4.3.3】版本
 - 重构了上传方法，可以随意切换本地上传和上传到七牛
 - 增加了文件删除方法，可以自由删除文件
 - 支持二次开发，添加其它的上传方式如 `aliyun OSS`等
 - 通过七牛 `fetch` 功能来抓取远程图片
 - 新增上传模式，[直传|服务器上传]，服务器上传是通过上传到服务器的临时文件再上传到七牛

#### 修复 

 - 修复同时上传不同文件夹同名称文件丢失问题，修复多文件同时上传丢失问题
 - 使用 `fetch` 方法来抓取远程图片
 - 修复老版本在线管理限定的1000个文件列表
 - 列表分页通过七牛传输的 `marker` 来进行查找分页


### 配置

> 配置两个文件，一个是 `php` 的配置文件 `config.php` 和 `Ueditor` 的配置文件 `config.json` ，默认的配置文件都在 `php` 目录下。


#### 本地上传配置 

> 修改 `config.php`

	'upload_type' => 'local',  // local 是上传到本地服务器
	'orderby'     => 'asc',    // 可选项 [desc|asc]列出文件的排序方式，此配置仅支持本地服务器
	'root_path'	  => $_SERVER['DOCUMENT_ROOT'],  // 本地上传的根目录地址

> 修改 `config.json`

	"uploadType" : "local", /* qiniu|local 【qiniu】七牛云存储 【local】本地上传*/

> 上传文件名称和保存路径可修改 `config.json` 中的配置信息，按照官网的配置就可以

#### 上传到七牛云存储 

> 修改 `config.php`

	'upload_type' => 'qiniu',    // qiniu 上传到七牛云存储服务器
	/* 七牛云存储信息配置 */
	'bucket'      => 'gitwiduu', // 七牛Bucket的名称
	'host'        => 'http://gitwiduu.u.qiniudn.com', // 七牛绑定的域名
	'access_key'  => 'KUN6xYZlOAtid2MjHm90-6VFY2M7HC90ijDH4uOR', // 七牛的access_key
	'secret_key'  => 'D-K57TE5hPe3krexftxLWFKmL2xbQEKA-mtkrUfB', // 七牛的secret_key

	/* 上传配置 */
	'timeout'     => '3600',  // 上传时间
	'save_type'   => 'date',  // 保存类型

	/* 水印设置 */
	'use_water'   => false,  // 是否开启水印
	/* 七牛水印图片地址 */
	'water_url'   => 'http://gitwiduu.u.qiniudn.com/ueditor-bg.png',

	/* 水印显示设置 */ 
	'dissolve'    => 50,  // 水印透明度
	'gravity'	  => 'SouthEast',  // 水印位置具体见文档图片说明和选项
	'dx'		  => 10,  //边距横向位置
	'dy'		  => 10   //边距纵向位置

> 修改 `config.json`

	/* 七牛云存储配置start */
	"uploadType" 	   : "qiniu",  /*  [qiniu]七牛云存储 */
	"qiniuUploadType"  : "url",    /*  [url|php] url 通过URL直传，根据token来判断返回地址, php 通过php文件方式传输 */
    "uploadQiniuUrl"   : "http://upload.qiniu.com/", /* 七牛上传地址 */
    "qiniuUploadPath"  : "uploads/",   /* 七牛上传的前缀 */
	"qiniuDatePath"    : "mmdd",       /* 自定义文件夹后的时间例如 uploads/0712 留空uploads/, 格式 yyyy == 2017 yy == 17 mm 月份 07 dd 日期 12 */
	"uploadSaveType"   : "date",       /* 保存文件的名称类型 */
	"getTokenActionName" : "getToken", /* 获取 Token 的方法 */

### 技术支持

邮箱 : admin@widuu.com

### 捐赠

本项目是个人业余时间开发和提供技术支持，欢迎捐赠！

![支付宝支付](./images/alipay.jpg)
![微信支付](./images/wechat.jpg)
