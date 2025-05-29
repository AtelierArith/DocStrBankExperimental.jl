```
Wrap <: BoundaryCondition

Wrap()
```

[`BoundaryCondition`](@ref) flag to wrap cordinates that boundary boundaries back to the opposite side of the grid.

Specifiy with:

```julia
ruleset = Ruleset(rule; boundary=Wrap())
# or
output = sim!(output, rule; boundary=Wrap())
```
