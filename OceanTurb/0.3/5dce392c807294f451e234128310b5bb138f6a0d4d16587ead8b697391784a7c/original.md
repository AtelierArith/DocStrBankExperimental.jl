```
BoundaryConditions([T=Float64;] bottom = GradientBoundaryCondition(-zero(T)),
                                   top = FluxBoundaryCondition(-zero(T)))
```

Returns `FieldBoundaryConditions` with a `bottom` and `top` boundary condition. The type `T` is only relevant for the default values of `bottom` and `top`.
