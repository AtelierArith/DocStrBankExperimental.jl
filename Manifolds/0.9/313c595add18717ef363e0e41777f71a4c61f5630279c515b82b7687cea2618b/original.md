```
Base.convert(::Type{Matrix{T}}, basis::CachedBasis{𝔽,DefaultOrthonormalBasis{𝔽, TangentSpaceType},HOSVDBasis{T, D}}) where {𝔽, T, D}
Base.convert(::Type{Matrix}, basis::CachedBasis{𝔽,DefaultOrthonormalBasis{𝔽, TangentSpaceType},HOSVDBasis{T, D}}) where {𝔽, T, D}
```

Convert a HOSVD-derived cached basis from [DewaeleBreidingVannieuwenhoven:2021](@cite) of the `D`th order [`Tucker`](@ref) manifold with number type `T` to a matrix. The columns of this matrix are the vectorisations of the [`embed`](@ref)dings of the basis vectors.
