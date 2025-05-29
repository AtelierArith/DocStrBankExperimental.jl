```
bounds(xs, [dims::Tuple]) => Tuple{Vararg{Tuple{T,T}}}
bounds(xs::Tuple) => Tuple{Vararg{Tuple{T,T}}}
bounds(x, dim) => Tuple{T,T}
bounds(dim::Union{Dimension,Lookup}) => Tuple{T,T}
```

オブジェクトのすべての次元、特定の次元、または次元のタプルの境界を返します。

境界が不明な場合、1つまたは両方の値は `nothing` である可能性があります。

`dims` は `Dimension`、次元タイプ、またはそのいずれかのタプルであることができます。
