```
basis_components([T=Float64,], e::ElectricFieldBasis, b::PolBasis)
```

電場基底ベクトル `e` の成分を偏光基底 `b` に関して含む静的ベクトルを返します。最初の引数は静的ベクトルの eltype でオプションです。

# 例

```julia
julia> basis_components(Float64, R(), PolBasis{XPol,Y}())
2-element StaticArraysCore.SVector{2, ComplexF64} with indices SOneTo(2):
 0.7071067811865475 + 0.0im
                0.0 - 0.7071067811865475im

julia> basis_components(R(), PolBasis{XPol,Y}())
2-element StaticArraysCore.SVector{2, ComplexF64} with indices SOneTo(2):
 0.7071067811865475 + 0.0im
                0.0 - 0.7071067811865475im


julia> basis_components(Float64, X(), PolBasis{XPol,Y}())
2-element StaticArraysCore.SVector{2, ComplexF64} with indices SOneTo(2):
 1.0 + 0.0im
 0.0 + 0.0im
```
