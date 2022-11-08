# 字蛛+（Font-spider-Plus）

Fork 之后改了配置文件

**font-spider-plus（字蛛+）是一个智能 WebFont 压缩工具，它能自动分析出本地页面和线上页面使用的 WebFont 并进行按需压缩。**
<p>
	<br>
	<img src="https://raw.githubusercontent.com/allanguys/font-spider-plus/master/README/fsp.gif" width="650">
	<br>
</p>

## 特性 ##

除了兼容font-spider（[字蛛](https://github.com/aui/font-spider/)）支持的特性：

1. 压缩字体：智能删除没有被使用的字形数据，大幅度减少字体体积
2. 生成字体：支持 woff2、woff、eot、svg 字体格式生成

font-spider-plus（字蛛+）还具有以下特性：

1. 支持线上动态渲染的页面
2. 支持线上GBK编码的文件

## 安装 ##
``` shell
    npm i font-spider-plus -g
``` 


## 使用范例 ##

### 一、书写 CSS
出自：[font-spider中文文档](https://github.com/aui/font-spider/blob/master/README-ZH-CN.md "font-spider中文文档")
``` css
/*声明 WebFont*/
@font-face {
  font-family: 'source';
  src: url('../font/source.eot');
  src:
    url('../font/source.eot?#font-spider') format('embedded-opentype'),
    url('../font/source.woff2') format('woff2'),
    url('../font/source.woff') format('woff'),
    url('../font/source.ttf') format('truetype'),
    url('../font/source.svg') format('svg');
  font-weight: normal;
  font-style: normal;
}

/*使用指定字体*/
.home h1, .demo > .test {
    font-family: 'source';
}
```

> 特别说明： `@font-face` 中的 `src` 定义的 .ttf 文件必须存在，其余的格式将由工具自动生成



### 二、压缩本地WebFont
``` shell
fsp local [options] <htmlFile1 htmlFile2 ...>
```
> 特别说明：htmlFile支持通配符，例如*.htm,*.shtml

### 三、压缩URL中的WebFont
#### 1、初始化fspconfig文件
``` shell
fsp init 
```
> 在根目录下生成fspconfig.json文件

#### 2、完善fspconfig.json文件
``` json
{
    /**
     * 本地font存放路径
     * @type    {String}
     */
    "localPath" : "../font/",
    /**
     * 线上字体文件路径 (网址中样式文件内font-family的src路径）
     * @type    {String}
     */
    "onlinePath" : "../font/",
    /**
     * URL
     * @type    {Array<String>}
     */
    "url" :  [
    "http://ieg.tencent.com/",
    "http://game.qq.com/"
     ]
}
```

#### 3、执行
``` shell
fsp run
```

## 相关链接


- [字蛛](https://github.com/aui/font-spider "font-spider")
- [字蛛API](https://github.com/aui/font-spider/blob/master/API.md "字蛛API")