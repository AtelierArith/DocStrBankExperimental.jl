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

与えられた条件を満たすすべての [`PathResult`](@ref) を返し、提供されている場合は関数 `f` を適用します。
