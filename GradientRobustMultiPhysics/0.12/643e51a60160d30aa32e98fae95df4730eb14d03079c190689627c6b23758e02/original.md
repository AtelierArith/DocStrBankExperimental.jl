```julia
DiagonalOperator(
;
    ...
) -> GradientRobustMultiPhysics.DiagonalOperator{Float64}
DiagonalOperator(
    value::Real;
    name,
    onlynz,
    regions
) -> GradientRobustMultiPhysics.DiagonalOperator{<:Real}

```

puts *value* on the diagonal entries of the cell dofs within given *regions*

if *onlyz* == true only values that are zero are changed

can only be applied in PDE LHS
