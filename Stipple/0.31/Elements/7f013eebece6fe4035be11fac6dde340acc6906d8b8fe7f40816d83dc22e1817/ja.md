```
@showif(expr, [type])
```

v-showは常にレンダリングされ、DOMに残ります; v-showは要素のdisplay CSSプロパティを切り替えるだけです。[https://vuejs.org/v2/guide/conditional.html#v-show](https://vuejs.org/v2/guide/conditional.html#v-show)

@showifと@iifの違い、どちらを使用するか

v-ifは切り替えコストが高く、v-showは初期レンダリングコストが高いです。

### 例

```julia
julia> h1("Hello!", @showif(:ok))
"<h1 v-show="ok">Hello!</h1>"
```
