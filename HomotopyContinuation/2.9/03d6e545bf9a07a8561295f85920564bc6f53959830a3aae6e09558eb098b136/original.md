```
results(
    result;
    only_real = false,
    real_tol = 1e-6,
    only_nonsingular = false,
    only_singular = false,
    only_finite = true,
    multiple_results = false,
)
results(f, result; options...)
```

Return all [`PathResult`](@ref)s for which satisfy the given conditions and apply, if provided, the function `f`.
