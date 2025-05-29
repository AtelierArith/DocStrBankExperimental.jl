```
score2pvalue(pwm, α, ϵ=1e-1, k=100, bg=[.25,.25,.25,.25])
```

Returns P-value(M,α) of a `pwm` with a given threshold `α`.

Input:

  * `pwm`: a 4 x m matrix
  * `α`: the score
  * `ϵ`: initial granularity  (optional)
  * `k`: Refinement parameter (optional)
  * `bg`: multinomial background (optional)

Output:

  * `pval`: p-value
