```
lookup(x::Dimension) => LookupArray
lookup(x, [dims::Tuple]) => Tuple{Vararg{LookupArray}}
lookup(x::Tuple) => Tuple{Vararg{LookupArray}}
lookup(x, dim) => LookupArray
```

次の[`LookupArray`](@ref)を返します。これは、配列の軸やインデックスの順序、サンプリングの特性など、次元の特性を決定します。

`dims`は、`Dimension`、次元タイプ、またはそのいずれかのタプルである可能性があります。
