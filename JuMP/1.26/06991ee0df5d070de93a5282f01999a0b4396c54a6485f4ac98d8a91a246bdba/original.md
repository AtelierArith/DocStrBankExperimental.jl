```
jump_function(model::AbstractModel, x::MOI.AbstractFunction)
```

Given an MathOptInterface object `x`, return the JuMP equivalent.

See also: [`moi_function`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> f = 2.0 * index(x) + 1.0
1.0 + 2.0 MOI.VariableIndex(1)

julia> jump_function(model, f)
2 x + 1
```
