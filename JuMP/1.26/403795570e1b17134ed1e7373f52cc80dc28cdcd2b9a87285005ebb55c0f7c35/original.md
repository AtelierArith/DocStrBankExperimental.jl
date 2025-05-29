```
remove_bridge(
    model::GenericModel{S},
    BT::Type{<:MOI.Bridges.AbstractBridge};
    coefficient_type::Type{T} = S,
) where {S,T}
```

Remove `BT{T}` from the list of bridges that can be used to transform unsupported constraints into an equivalent formulation using only constraints supported by the optimizer.

See also: [`add_bridge`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> add_bridge(model, MOI.Bridges.Constraint.SOCtoNonConvexQuadBridge)

julia> remove_bridge(model, MOI.Bridges.Constraint.SOCtoNonConvexQuadBridge)

julia> add_bridge(
           model,
           MOI.Bridges.Constraint.NumberConversionBridge;
           coefficient_type = Complex{Float64},
       )

julia> remove_bridge(
           model,
           MOI.Bridges.Constraint.NumberConversionBridge;
           coefficient_type = Complex{Float64},
       )
```
