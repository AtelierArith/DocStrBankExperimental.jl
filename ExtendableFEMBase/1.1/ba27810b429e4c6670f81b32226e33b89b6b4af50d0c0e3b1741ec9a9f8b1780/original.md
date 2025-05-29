```julia
ref_integrate!(
    integral::AbstractArray,
    EG::Type{<:ExtendableGrids.AbstractElementGeometry},
    order::Int64,
    integrand::Function
)

```

Integration for reference basis functions on reference domains (merely for testing stuff).

Note: area of reference geometry is not multiplied
