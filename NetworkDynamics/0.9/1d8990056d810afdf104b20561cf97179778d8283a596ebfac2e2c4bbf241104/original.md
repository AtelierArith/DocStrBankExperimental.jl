```
initialize_component!(cf::ComponentModel; verbose=true, apply_bound_transformation=true, kwargs...)
```

Initialize a `ComponentModel` by solving the corresponding `NonlinearLeastSquaresProblem`. During initialization, everyting which has a `default` value (see [Metadata](@ref)) is considered "fixed". All other variables are considered "free" and are solved for. The initial guess for each variable depends on the `guess` value in the [Metadata](@ref).

The result is stored in the `ComponentModel` itself. The values of the free variables are stored in the metadata field `init`.

The `kwargs` are passed to the nonlinear solver.

## Bounds of free variables

When encountering any bounds in the free variables, NetworkDynamics will try to conserve them by applying a coordinate transforamtion. This behavior can be supressed by setting `apply_bound_transformation`. The following transformations are used:

  * (a, b) intervals where both a and b are positive are transformed to `u^2`/`sqrt(u)`
  * (a, b) intervals where both a and b are negative are transformed to `-u^2`/`sqrt(-u)`
