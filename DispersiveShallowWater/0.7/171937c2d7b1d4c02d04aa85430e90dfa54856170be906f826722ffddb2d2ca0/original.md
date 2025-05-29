```
lake_at_rest_error(q, equations)
```

Calculate the error for the "lake-at-rest" test case where the [`waterheight_total`](@ref) $\eta = h + b$ should be a constant value over time (given by the value $\eta_0$ passed to the `equations` when constructing them).
