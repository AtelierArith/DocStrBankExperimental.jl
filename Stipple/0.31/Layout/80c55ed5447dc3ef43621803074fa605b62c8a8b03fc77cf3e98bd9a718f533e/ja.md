```
function column(args...; size=-1, xs=-1, sm=-1, md=-1, lg=-1, xl=-1, kwargs...)
```

QuasarのFlexgrid CSSクラス`column`を持つ`div` HTML要素を作成します。このようなカラムには、通常、[`cell`](@ref)、[`row`](@ref)、`column`、または手動でグリッドクラスを受け取る他の要素（例：`"col"`、`"col-sm-5"`）が含まれます。

グリッドサイズのキーワード引数`size`、`xs`などについては、[`cell`](@ref)のドキュメントで詳しく説明されています。

### 例

```julia
julia> column(span("Hello"))
"<div class="column"><span>Hello</span></div>"
```
