```
set_graph_property!(g, name, x)
```

プロパティ `name` を値 `x` に設定します。プロパティが存在しない場合は作成します。 [`gprop!`](@ref) はこの関数の短縮形として便利に使用できます。

**例**

```julia
g = Network(10, 20)
set_graph_property!(g, "label", "My Network")
# または同等に
gprop!(g, "label", "My Network")
```
