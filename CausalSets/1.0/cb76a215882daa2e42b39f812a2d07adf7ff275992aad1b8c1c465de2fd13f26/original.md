```
bd_chain_coef_along(causet, i, j, dim, locality, ::Val{N}[, max_cardinality])
```

Return the sum of the Benincasa-Dowker chain coefficients for all chains with length `N+1` that have starting point `i` and ending point `j`, i.e. return the coefficient for the BD^`N` operator between `i` and `j`.
