```julia
get_basissubset(
    ::Type{<:ExtendableGrids.AssemblyType},
    FE::ExtendableFEMBase.FESpace{Tv, Ti, FEType<:ExtendableFEMBase.AbstractFiniteElement, APT},
    ::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> ExtendableFEMBase.var"#closure#268"{_A, Int64} where _A
get_basissubset(
    ::Type{<:ExtendableGrids.AssemblyType},
    FE::ExtendableFEMBase.FESpace{Tv, Ti, FEType<:ExtendableFEMBase.AbstractFiniteElement, APT},
    ::Type{<:ExtendableGrids.AbstractElementGeometry},
    xgrid
) -> Union{ExtendableFEMBase.var"#21#22", ExtendableFEMBase.var"#closure#277"{_A, _B, _C, Int64, Int64} where {_A, _B, _C}}

```

は次の形式のクロージャ関数を返します。

```
closure(subset_ids::Array{Int, 1}, cell)
```

これはセル上で必要なローカル基底関数のIDを返します。通常、subset_ids = 1:ndofs（つまり、参照セル上のすべての基底関数が使用されることを意味します）、

例えば、異なる基底関数が面の向きに応じて選択される3DのBDM1またはH1P3の実装を参照してください（3Dでは単に符号だけではありません）。
