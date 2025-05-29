```
bd_chain_coef_along(causet, chain, dim, dim, locality locality[, max_cardinality]) -> Float64
```

Return the Benincasa-Dowker chain coefficient for the chain `chain` in `causet`, i.e. the product of the individual BD coefficients between the steps of the chain. If `chain` is not a chain, return `0`.
