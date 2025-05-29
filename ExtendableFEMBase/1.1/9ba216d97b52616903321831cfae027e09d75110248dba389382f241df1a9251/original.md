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

returns the coefficients for local evaluations of finite element functions ( see e.g. h1v_br.jl for a use-case)
