```
setindex(d::AbstractSmallDict{N,K,V}, val, key) where {N,K,V} -> Tuple{SmallDict{N,K,V}, V}
```

`d`から`key => val`のマッピングを追加することによって得られる辞書を返します。

また、`Base.setindex!`や[`push`](@ref push(::AbstractSmallDict, ::Pair))も参照してください。
