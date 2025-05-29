```
bd_coef_field_from(causet, j, dim, locality[, max_cardinality]) -> Vector{Float64}
```

Return the Benincasa-Dowker coefficient field for the BD operator applied at spacetime atom `j`. The resulting vector has length `j`, such that the `i`th entry corresponds to the coefficient of spacetime atom `i`.
