```
pop(d::AbstractSmallDict{N,K,V}, key) where {N,K,V} -> Tuple{SmallDict{N,K,V}, V}
```

`d`から`key`のマッピングを削除し、新しい辞書と`d[key]`の値を返します。

また、`Base.pop!`、[`delete`](@ref delete(::AbstractSmallDict, ::Any))も参照してください。
