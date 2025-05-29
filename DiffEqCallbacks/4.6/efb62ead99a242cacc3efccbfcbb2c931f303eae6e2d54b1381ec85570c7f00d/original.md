```julia
IntegratingCallback(integrand_func,
    integrand_values::IntegrandValues, integrand_prototype)
```

Let one define a function `integrand_func(u, t, integrator)::typeof(integrand_prototype)` which returns Integral(integrand_func(u(t),t)dt over the problem tspan.

## Arguments

  * `integrand_func(out, u, t, integrator)` for in-place problems and `out = integrand_func(u, t, integrator)` for out-of-place problems. Returns the quantity in the integral for computing dG/dp. Note that for out-of-place problems, this should allocate the output (not as a view to `u`).
  * `integrand_values::IntegrandValues` is the types that `integrand_func` will return, i.e. `integrand_func(t, u, integrator)::integrandType`. It's specified via `IntegrandValues(integrandType)`, i.e. give the type that `integrand_func` will output (or higher compatible type).
  * `integrand_prototype` is a prototype of the output from the integrand.

The outputted values are saved into `integrand_values`. The values are found via `integrand_values.integrand`.

!!! note
    This method is currently limited to ODE solvers of order 10 or lower. Open an issue if other solvers are required.

    If `integrand_func` is in-place, you must use `cache` to store the output of `integrand_func`.

