```julia
ConvectionRotationFormOperator(
    beta::Int64,
    beta_operator::Type{<:??},
    xdim::Int64,
    ncomponents::Int64;
    name,
    AT,
    factor,
    ansatz_operator,
    test_operator,
    regions
)

```

constructor for a bilinearform a(u,v) = (beta x curl(u),v) where beta is the id of some unknown vector field of the PDEDescription, u and v are also vector-fields and x is the cross product (so far this is only implemented in 2D)
