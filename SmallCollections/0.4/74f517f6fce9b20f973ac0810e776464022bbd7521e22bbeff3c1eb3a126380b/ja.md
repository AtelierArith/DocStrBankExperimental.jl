```
push(s::AbstractSmallSet{N,T}, xs...) where {N,T} -> Tuple{SmallSet{N,T}, T}
```

引数として与えられた要素を追加することによって `s` から得られる集合を返します。

関連情報として `Base.push!` も参照してください。
