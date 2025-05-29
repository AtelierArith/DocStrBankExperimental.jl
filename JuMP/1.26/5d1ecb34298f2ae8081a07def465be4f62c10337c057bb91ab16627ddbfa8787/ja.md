```
set_normalized_coefficients(
    constraint::ConstraintRef{<:AbstractModel,<:MOI.ConstraintIndex{F}},
    variable::AbstractVariableRef,
    new_coefficients::Vector{Tuple{Int64,T}},
) where {T,F<:Union{MOI.VectorAffineFunction{T},MOI.VectorQuadraticFunction{T}}}
```

非推奨のメソッドで、現在は [`set_normalized_coefficient`](@ref) にリダイレクトされます。
