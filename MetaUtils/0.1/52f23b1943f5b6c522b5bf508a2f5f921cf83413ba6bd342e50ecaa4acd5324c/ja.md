```
@show_tree(expr, maxdepth=10, linenums=false)
```

は、式 `expr` のツリー形式を maxdepth で表示し、`linenums` が true の場合は行番号ノードを印刷します。

## 例

```julia
julia> @show_tree 2x+1
:call
├─ :+
├─ :call
│  ├─ :*
│  ├─ 2
│  └─ :x
└─ 1
```
