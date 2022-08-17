# Sass
## Sass [Syntactically Awesome StyleSheets]
简介：Sass 是一款强化的css的辅助工具，其在css的语法上增加了变量，嵌套，混合，导入等高级功能。特征扩展使css更加的强大与优雅。使用sass以及sass的样式库有助于更好额组织管理样式文件。

## 使用变量
将反复使用的css的属性值定义为变量，无需重复书写该值，或者通过对某一个属性值定义为变量，并且可赋予其一个易懂的名称。做到见名知意
### 语法
[$ | ! 其中的！一般使用在老版本中]标识变量。
### 变量的声明与应用
#### 声明变量
```$light-color:#F90;```
#### 使用变量
```nav {color:$light-color:#F90;}```

#### 变量的默认值
一般状况在多次重复定义一个变量时，会导致之前创建的变量会被覆盖。使用默认值时
```
$fancybox-width: 400px !default;
.fancybox {
width: $fancybox-width;
}

```
注意点：
- 变量可以与css中的属性名称一致

## 嵌套css 规则
css 中的重复选择器
- 传统的定义嵌套css样式的方式

```
#content article h1 { color: #333 }
#content article p { margin-bottom: 1.4em }
#content aside { background-color: #EEE }

```
- 使用sass后
  
```
#content {
  article {
    h1 { color: #333 }
    p { margin-bottom: 1.4em }
  }
  aside { background-color: #EEE }
}

```
注意点：
1.默认在使用嵌套的sass语法定义的样式后，在其编译解析后，会一次使用空格将样式表进行拼接
2. 在嵌套中除了属性值可以进行嵌套操作外，还可以对属性进行嵌套定义
```
nav {
    border: {
        style:solid;
        width:1px;
        color:#ccc
    }
}

```
冒号：解析规则。默认与其{}中定义的属性关联[解析后]
```
nav { 
    border-style:solid;
    border-width:1px;
    border-color:#ccc;
}

```
## 导入sass文件
在css 中存在一个语法特性@import 用于将外部的css文件导入到其他的css文件。但其只有在浏览器加载到@import时，对应的文件才会被导入
但是，在sass中@import 在生成css文件时，就已经将对对应的css文件导入。
### Sass局部文件：
sass的局部文件是以下划线开头，这样在sass文件编译时不会将该文件作为单独的文件css输出。而只把该文件作为局部文件导入。

##  混合器
需要大段的使用类似的样式代码，可使用混合器的方式实现
关键字`@mixin`
```
@mixin rounded-corners {
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
```
使用关键字`@mixin`的方式定义快寄的重复使用样式表

使用`@include`的方式进行载入
```
notice {
  background-color: green;
  border: 2px solid #00aa00;
  @include rounded-corners;
}

```
编译后的css
```
notice {
  background-color: green;
  border: 2px solid #00aa00;
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
```

使用混合样式，可以在不同模块中共享样式。如存在不停重复一段css代码时则应该使用混合模式进行重构。



