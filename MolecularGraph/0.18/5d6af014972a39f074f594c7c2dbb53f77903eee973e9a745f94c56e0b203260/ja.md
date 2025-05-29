```
maximum_conn_clique(::Type{U}, g::SimpleGraph{T}, eattrs::Dict;
    kwargs...) where {T,U} -> (U, Symbol)
```

最大接続クリークを計算します。
