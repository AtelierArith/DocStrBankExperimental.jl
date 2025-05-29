```
Semiinteger(lower, upper)
```

A short-cut for the [`MOI.Semiinteger`](@ref) set.

This short-cut is useful because it automatically promotes `lower` and `upper` to the same type, and converts them into the element type supported by the JuMP model.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x in Semiinteger(3, 5))
x

julia> print(model)
Feasibility
Subject to
 x ∈ MathOptInterface.Semiinteger{Int64}(3, 5)
```
