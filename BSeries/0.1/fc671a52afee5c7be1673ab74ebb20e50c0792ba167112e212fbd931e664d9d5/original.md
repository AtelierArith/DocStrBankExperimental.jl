```
is_symplectic(series_integrator; kwargs...)::Bool
```

This function checks whether the B-series `series_integrator` of a time integration method is symplectic (conserves quadratic invariants) - up to the [`order`](@ref) of `series_integrator`.

By default, the comparison of the coefficients entering the conditions is performed using `isequal`. If keyword arguments such as absolute/relative tolerances `atol`/`rtol` are given or floating point numbers are used, the comparison is performed using `isapprox` and the keyword arguments `kwargs...` are forwarded.

See also [`order_of_symplecticity`](@ref).
