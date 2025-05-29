```
function row(args...; size=-1, xs=-1, sm=-1, md=-1, lg=-1, xl=-1, kwargs...)
```

QuasarのFlexgrid CSSクラス`row`を持つ`div` HTML要素を作成します。このような行には通常、[`cell`](@ref)、`row`、[`column`](@ref)または手動でグリッドクラスを受け取る他の要素（例：`"col"`、`"col-sm-5"`）で作成された要素が含まれます。

グリッドサイズのkwargs `size`、`xs`などについては、[`cell`](@ref)のドキュメントで詳しく説明されています。

### 例

```julia
julia> row(span("Hello"))
"<div class="row"><span>Hello</span></div>"
```
