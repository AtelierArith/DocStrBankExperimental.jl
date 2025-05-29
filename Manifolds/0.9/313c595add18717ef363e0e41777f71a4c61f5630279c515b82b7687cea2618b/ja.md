```
Base.convert(::Type{Matrix{T}}, basis::CachedBasis{𝔽,DefaultOrthonormalBasis{𝔽, TangentSpaceType},HOSVDBasis{T, D}}) where {𝔽, T, D}
Base.convert(::Type{Matrix}, basis::CachedBasis{𝔽,DefaultOrthonormalBasis{𝔽, TangentSpaceType},HOSVDBasis{T, D}}) where {𝔽, T, D}
```

HOSVDに由来するキャッシュされた基底を、数値型 `T` の [`Tucker`](@ref) 多様体の `D` 次元から行列に変換します。この行列の列は、基底ベクトルの [`embed`](@ref)dings のベクトル化です。
