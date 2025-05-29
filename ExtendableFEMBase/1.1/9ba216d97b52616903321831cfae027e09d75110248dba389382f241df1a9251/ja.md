```julia
get_coefficients(
    ::Type{<:ExtendableGrids.AssemblyType},
    FE::ExtendableFEMBase.FESpace{Tv, Ti, FEType<:ExtendableFEMBase.AbstractFiniteElement, APT},
    ::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> ExtendableFEMBase.var"#closure#227"
get_coefficients(
    ::Type{<:ExtendableGrids.AssemblyType},
    FE::ExtendableFEMBase.FESpace{Tv, Ti, FEType<:ExtendableFEMBase.AbstractFiniteElement, APT},
    ::Type{<:ExtendableGrids.AbstractElementGeometry},
    xgrid
) -> ExtendableFEMBase.var"#closure#118"

```

有限要素関数のローカル評価のための係数を返します（使用例については、h1v_br.jlを参照してください）。
