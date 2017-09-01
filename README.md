
![](https://github.com/CarGuo/LazyRecyclerAdapter/blob/master/22.png)

### 这个一个极简的通用RecyclerView的适配器，让你普通的RecyclerView变得灵活、解耦、通用、丰富起来吧。

[![](https://jitpack.io/v/CarGuo/LazyRecyclerAdapter.svg)](https://jitpack.io/#CarGuo/LazyRecyclerAdapter)
[![Build Status](https://travis-ci.org/CarGuo/LazyRecyclerAdapter.svg?branch=master)](https://travis-ci.org/CarGuo/LazyRecyclerAdapter)


状态 | 功能
-------- | ---
**支持**|**系统RecyclerView和任意数据实体**
**支持**|**动态加载各种Item类型的列表、瀑布流、网格**
**支持**|**列表、瀑布流、网格的刷新和加载更多效果，支持上下左右各个方向**
**支持**|**自定义刷新和加载效果**
**支持**|**内置支持各种列表和方向的万能分割线**
**支持**|**点击和长按效果**
**支持**|**空页面**
**支持**|**Item的动画效果**
**支持**|**Header头支持**
**支持**|**一种数据实体对应多种Item**



#### 在你的项目project下的build.gradle添加
```
allprojects {
	repositories {
		...
		maven { url 'https://jitpack.io' }
	}
}
```
#### 在module下的build.gradle添加依赖
```
dependencies {
    compile 'com.github.CarGuo:LazyRecyclerAdapter:v3.0.0'
}

```


## [wiki 文档](https://github.com/CarGuo/LazyRecyclerAdapter/wiki)

--------------------------------------------------------------------------------


### 效果
<div>
<img src="https://github.com/CarGuo/CommonRecycler/blob/master/12.png" width="120px" height="218px"/>
<img src="https://github.com/CarGuo/CommonRecycler/blob/master/13.png" width="120px" height="218px"/>
<img src="https://github.com/CarGuo/CommonRecycler/blob/master/14.png" width="120px" height="218px"/>
</div>

### 使用方法

1、创建管理器

管理器绑定数据、布局、Holder。其中XXXHolder需要继承BindRecyclerBaseHolder。

BindRecyclerBaseHolder时继承了RecyclerView.ViewHolder的基类。

```
//创建管理器
BindSuperAdapterManager normalAdapterManager = new BindSuperAdapterManager();
//将数据Model类、布局layoutId、RecyclerView.ViewHolder绑定
normalAdapterManager
        .bind(BindImageModel.class, R.layout.horizontal_image_item, BindImageHolder.class)
        .bind(BindTextModel.class, R.layout.horizontal_text_item, BindTextHolder.class)
        .bind(BindClickModel.class, R.layout.horizontal_click_item, BindClickHolder.class)
        .bindEmpty(BindNoDataHolder.NoDataModel.class, BindNoDataHolder.ID, BindNoDataHolder.class)
```

2、创建Adapter，设置RecyclerView
```
//通过管理器构建Adapter
BindSuperAdapter adapter = new BindSuperAdapter(context, normalAdapterManager, datas);

recycler.setLayoutManager(staggeredGridLayoutManager);
recycler.setAdapter(adapter);

```

更多高级用法请看Demo与[wiki 文档](https://github.com/CarGuo/LazyRecyclerAdapter/wiki)。

### License

本项目把XRecyclerView的部分功能拆解到Adapter中
```
MIT

```