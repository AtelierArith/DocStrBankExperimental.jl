```
Parameter(value)
```

A short-cut for the [`MOI.Parameter`](@ref) set.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x in Parameter(2))
x

julia> print(model)
Feasibility
Subject to
 x ∈ MathOptInterface.Parameter{Float64}(2.0)
```
