```
set_bcs!(model; bcspecs...)
```

Set boundary conditions of model solution fields. The keyword argument name must be the name of a model solution and its value is a (bottom*bc, top*bc) tuple.

# Example

julia> set_bcs!(model, c=(FluxBoundaryCondition(-1),                           FluxBoundaryCondition(0))                 )
