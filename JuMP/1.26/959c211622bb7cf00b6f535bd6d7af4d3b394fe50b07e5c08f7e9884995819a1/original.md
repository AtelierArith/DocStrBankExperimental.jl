```
value_type(::Type{<:Union{AbstractModel,AbstractVariableRef}})
```

Return the return type of [`value`](@ref) for variables of that model. It defaults to `Float64` if it is not implemented.

## Example

```jldoctest
julia> value_type(GenericModel{BigFloat})
BigFloat
```
