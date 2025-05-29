```julia
FESpaces(
    FEV::ExtendableFEMBase.FEVector{T, Tv, Ti}
) -> Vector{T} where T<:(ExtendableFEMBase.FESpace{_A, _B} where {_B, _A})

```

与えられたFEVectorのブロックのFEspaceのベクトルを返します。
