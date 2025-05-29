```
order_of_accuracy(series; kwargs...)
```

Determine the order of accuracy of the B-series `series`. By default, the comparison with the coefficients of the exact solution is performed using `isequal`. If keyword arguments such as absolute/relative tolerances `atol`/`rtol` are given or floating point numbers are used, the comparison is performed using `isapprox` and the keyword arguments `kwargs...` are forwarded.

See also [`order`](@ref), [`ExactSolution`](@ref), [`order_of_symplecticity`](@ref).
