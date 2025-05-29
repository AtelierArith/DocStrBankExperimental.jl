```
add_vertex_property!(g, name, T)
add_vertex_property!(g, name, vmap)
```

グラフ `g` に頂点プロパティ `name` を追加します。

型 `T` が入力として与えられた場合、値の型 `T` を持つ頂点マップが作成され、`g` に保存されます。

代わりに、既存の頂点マップ `vmap` を `g` に保存することもできます。

[`vprop!`](@ref) はこの関数の短縮形です。
