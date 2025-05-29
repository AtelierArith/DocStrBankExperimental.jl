```
setindex(v::AbstractFixedVector{N,T}, x, i::Integer) where {N,T} -> FixedVector{N,T}
```

`v`の`i`番目の成分を`x`に置き換え、結果を返します。ベクトル`v`は変更されません。

また、`Base.setindex`、[`addindex`](@ref addindex(::AbstractFixedVector, ::Any, ::Integer))も参照してください。
