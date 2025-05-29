```
Semicontinuous(lower, upper)
```

A short-cut for the [`MOI.Semicontinuous`](@ref) set.

This short-cut is useful because it automatically promotes `lower` and `upper` to the same type, and converts them into the element type supported by the JuMP model.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x in Semicontinuous(1, 2))
x

julia> print(model)
Feasibility
Subject to
 x ∈ MathOptInterface.Semicontinuous{Int64}(1, 2)
```
