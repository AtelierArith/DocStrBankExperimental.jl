```
jump_function_type(model::AbstractModel, ::Type{T}) where {T}
```

Given an MathOptInterface object type `T`, return the JuMP equivalent.

See also: [`moi_function_type`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> jump_function_type(model, MOI.ScalarAffineFunction{Float64})
AffExpr (alias for GenericAffExpr{Float64, GenericVariableRef{Float64}})
```
