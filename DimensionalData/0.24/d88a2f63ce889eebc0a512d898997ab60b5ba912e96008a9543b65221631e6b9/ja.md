```
bounds(xs, [dims::Tuple]) => Tuple{Vararg{Tuple{T,T}}}
bounds(xs::Tuple) => Tuple{Vararg{Tuple{T,T}}}
bounds(x, dim) => Tuple{T,T}
bounds(dim::Union{Dimension,LookupArray}) => Tuple{T,T}
```

オブジェクトのすべての次元、特定の次元、または次元のタプルの境界を返します。

`dims` は `Dimension`、次元タイプ、またはそのいずれかのタプルである可能性があります。
