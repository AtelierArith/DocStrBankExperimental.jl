```
PrescribedVelocityFields(; u = ZeroField(),
                           v = ZeroField(),
                           w = ZeroField(),
                           parameters = nothing)
```

Builds `PrescribedVelocityFields` with prescribed functions `u`, `v`, and `w`.

If `isnothing(parameters)`, then `u, v, w` are called with the signature

```
u(x, y, z, t) = # something interesting
```

If `!isnothing(parameters)`, then `u, v, w` are called with the signature

```
u(x, y, z, t, parameters) = # something parameterized and interesting
```

In the constructor for `HydrostaticFreeSurfaceModel`, the functions `u, v, w` are wrapped in `FunctionField` and associated with the model's `grid` and `clock`.
