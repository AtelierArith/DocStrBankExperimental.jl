```
pval2score(pwm, pval, ϵ=1e-1, k=10, bg=[.25,.25,.25,.25])
```

Returns the highest score(M,pval) of a `pwm` such that p-value is greater or equal to `pval`.

Input:

  * `pwm`: a 4 x m matrix
  * `pval`: a p-value; e.g. pval = 1e-3
  * `ϵ`: initial granularity  (optional)
  * `k`: Refinement parameter (optional)
  * `bg`: multinomial background (optional)

Output    

  * `α`: the highest score-threshold
