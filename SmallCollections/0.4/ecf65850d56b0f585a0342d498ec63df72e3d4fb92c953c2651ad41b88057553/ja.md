```
pop(s::AbstractSmallSet{N,T}, x) where {N,T} -> Tuple{SmallSet{N,T}, T}
```

要素 `x` を `s` から削除し、新しいセットと `x` に等しい格納された要素を返します。

`Base.pop!` や [`delete`](@ref delete(::AbstractSmallSet, ::Any)) も参照してください。
