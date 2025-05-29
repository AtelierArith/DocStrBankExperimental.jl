```
Optimisers.init(rule::RuleType, parameters) -> state
```

Sets up the initial state for a given optimisation rule, and an array of parameters. This and [`apply!`](@ref Optimisers.apply!) are the two functions which any new optimisation rule must define.

# Examples

```jldoctest
julia> Optimisers.init(Descent(), Float32[1,2,3])  # is `nothing`

julia> Optimisers.init(Momentum(), [1.0, 2.0])
2-element Vector{Float64}:
 0.0
 0.0
```
