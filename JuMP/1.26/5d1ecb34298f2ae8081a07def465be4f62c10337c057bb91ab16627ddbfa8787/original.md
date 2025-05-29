```
set_normalized_coefficients(
    constraint::ConstraintRef{<:AbstractModel,<:MOI.ConstraintIndex{F}},
    variable::AbstractVariableRef,
    new_coefficients::Vector{Tuple{Int64,T}},
) where {T,F<:Union{MOI.VectorAffineFunction{T},MOI.VectorQuadraticFunction{T}}}
```

A deprecated method that now redirects to [`set_normalized_coefficient`](@ref).
