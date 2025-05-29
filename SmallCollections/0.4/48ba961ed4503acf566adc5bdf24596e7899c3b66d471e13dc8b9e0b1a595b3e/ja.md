```
push(d::AbstractSmallDict{N,K,V}, key1 => val1, key2 => val2, ...) where {N,K,V} -> Tuple{SmallDict{N,K,V}, V}
```

引数として与えられたマッピングを追加することによって得られる辞書を返します。

また、`Base.push!`、[`setindex`](@ref setindex(::AbstractSmallDict, ::Any, ::Any))も参照してください。
