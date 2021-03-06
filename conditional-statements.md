# 条件语句

你可能早已知晓，Sass通过`@if`和`@else`指令提供了条件语句。除非你的代码中有偏复杂的逻辑，否则没必要在日常开发的样式表中使用条件语句。实际上，条件语句主要适用于库和框架。

无论何时，如果你感觉需要它们，请遵守下述准则：

* 除非必要，不然不需要括号；
* 务必在左开大括号(`{`)后换行；
* `@else`语句和它前面的右闭大括号(`}`)写在同一行。

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
```scss
// 推荐范式
@if $support-legacy {
  // ...
} @else {
  // ...
}

// 不推荐范式
@if ($support-legacy == true) {
  // ...
}
@else {
  // ...
}
```
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
```sass
// 推荐范式
@if $support-legacy
  // ...
@else
  // ...

// 不推荐范式
@if ($support-legacy == true)
  // ...
@else
  // ...
```
  </div>
</div>

测试一个错误值时，通常使用`not`关键字而不是比较与`false`或`null`等值。

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
```scss
// 推荐范式
@if not index($list, $item) {
  // ...
}

// 不推荐范式
@if index($list, $item) == null {
  // ...
}
```
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
```sass
// 推荐范式
@if not index($list, $item)
  // ...

// 不推荐范式
@if index($list, $item) == null
  // ...
```
  </div>
</div>

当使用条件语句并在一些条件下有内联函数返回不同结果时，始终要确保最外层函数有一个`@return`语句。

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
```scss
// 推荐范式
@function dummy($condition) {
  @if $condition {
    @return true;
  }

  @return false;
}

// 不推荐范式
@function dummy($condition) {
  @if $condition {
    @return true;
  } @else {
    @return false;
  }
}
```
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
```sass
// 推荐范式
@function dummy($condition)
  @if $condition
    @return true

  @return false;

// 不推荐范式
@function dummy($condition)
  @if $condition
    @return true
  @else
    @return false
```
  </div>
</div>
