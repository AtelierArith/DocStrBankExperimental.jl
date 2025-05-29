```
lookup(x::Dimension) => Lookup
lookup(x, [dims::Tuple]) => Tuple{Vararg{Lookup}}
lookup(x::Tuple) => Tuple{Vararg{Lookup}}
lookup(x, dim) => Lookup
```

次の[`Lookup`](@ref)を返します。これは、配列の軸や検索順序、サンプリング特性など、次元の特性を決定します。

`dims`は`Dimension`、次元型、またはそのいずれかのタプルである可能性があります。

これは`val`とは異なり、次元が実際に`AbstractArray`の検索を含む場合にのみ機能し、`DimArray`または`DimStack`で使用してすべての検索を取得できます。これは、`val`に関して意味のあいまいさがないためです。
