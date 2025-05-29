```
order_of_symplecticity(series_integrator; kwargs...)
```

Determine the order of symplecticity of the B-series `series_integrator`, i.e., the order up to which quadratic invariants are conserved. By default, the comparison of the coefficients entering the conditions is performed using `isequal`. If keyword arguments such as absolute/relative tolerances `atol`/`rtol` are given or floating point numbers are used, the comparison is performed using `isapprox` and the keyword arguments `kwargs...` are forwarded.

See also [`is_symplectic`](@ref), [`order`](@ref), [`order_of_accuracy`](@ref).
