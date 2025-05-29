```julia
VertexRule(
    ET::Type{ExtendableGrids.Edge1D};
    ...
) -> ExtendableFEMBase.SQuadratureRule{Float64, ExtendableGrids.Edge1D, 1}
VertexRule(
    ET::Type{ExtendableGrids.Edge1D},
    order;
    T
) -> ExtendableFEMBase.SQuadratureRule{Float64, ExtendableGrids.Edge1D, 1}

```

sets up a quadrature rule that evaluates at vertices of element geometry; not optimal from quadrature point of view, but helpful when interpolating. Note, that order of xref matches dof order of H1Pk element
