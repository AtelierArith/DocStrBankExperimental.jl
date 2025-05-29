```julia
FESpaces(
    FEV::GradientRobustMultiPhysics.FEVector{T, Tv, Ti}
) -> Vector{T} where T<:(GradientRobustMultiPhysics.FESpace{_A, _B} where {_B, _A})

```

与えられたFEVectorのブロックのFE空間のベクトルを返します。
