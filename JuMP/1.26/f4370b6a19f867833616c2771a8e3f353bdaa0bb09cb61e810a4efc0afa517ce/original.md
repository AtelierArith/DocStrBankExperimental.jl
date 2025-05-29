```
moi_function(x::AbstractJuMPScalar)
moi_function(x::AbstractArray{<:AbstractJuMPScalar})
```

Given a JuMP object `x`, return the MathOptInterface equivalent.

See also: [`jump_function`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> f = 2.0 * x + 1.0
2 x + 1

julia> moi_function(f)
1.0 + 2.0 MOI.VariableIndex(1)
```
