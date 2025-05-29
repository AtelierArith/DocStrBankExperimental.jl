```
addindex(v::AbstractFixedVector{N,T}, x, i::Integer) where {N,T} -> FixedVector{N,T}
```

`v`の`i`-番目の成分に`x`を加え、結果を返します。ベクトル`v`は変更されません。

[`setindex`](@ref setindex(::AbstractFixedVector, ::Any, ::Integer))も参照してください。
