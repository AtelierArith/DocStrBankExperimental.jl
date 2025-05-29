```
findzero(f, bracket; atol=1e-7, max_iter=100)
findzero(f, method::AbstractBisection; atol=1e-7, max_iter=100)
```

Find roots using the passed in method. If a bracket is passed in without specifying the method, use the [`Secant`](@ref) method.
