```
add_edge_property!(g, name, T)
add_edge_property!(g, name, emap)
```

グラフ `g` にエッジプロパティ `name` を追加します。

型 `T` が入力として与えられた場合、値の型 `T` を持つエッジマップが作成され、`g` に保存されます。

代わりに、既存のエッジマップ `emap` を `g` に保存することもできます。

[`eprop!`](@ref) はこの関数の短縮形です。

**例**

```julia
g = random_regular_graph(10, 3, Network)

add_edge_property!(g, "weight", Float64)
# または同等に
eprop!(g, "weight", Float64)
```
