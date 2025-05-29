```
Remove <: BoundaryCondition

Remove()
```

[`BoundaryCondition`](@ref) flag that specifies to assign `padval` to cells that overflow  grid boundaries. `padval` defaults to `zero(eltype(grid))` but can be assigned as a keyword argument to an [`Output`](@ref).

Specifiy with:

```julia
ruleset = Ruleset(rule; boundary=Remove())
# or
output = sim!(output, rule; boundary=Remove())
```
