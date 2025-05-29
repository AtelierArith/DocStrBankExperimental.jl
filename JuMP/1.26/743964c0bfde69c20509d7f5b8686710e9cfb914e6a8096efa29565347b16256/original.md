```
add_bridge(
    model::GenericModel{T},
    BT::Type{<:MOI.Bridges.AbstractBridge};
    coefficient_type::Type{S} = T,
) where {T,S}
```

Add `BT{T}` to the list of bridges that can be used to transform unsupported constraints into an equivalent formulation using only constraints supported by the optimizer.

See also: [`remove_bridge`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> add_bridge(model, MOI.Bridges.Constraint.SOCtoNonConvexQuadBridge)

julia> add_bridge(
           model,
           MOI.Bridges.Constraint.NumberConversionBridge;
           coefficient_type = Complex{Float64}
       )
```
