```
twovar_marginals(A::AbstractTensorTrain; l, r, M, Δlmax)
```

Compute the marginal distributions for each pair of sites $p(x^l, x^m)$

### Optional arguments

  * `l = accumulate_L(A)[1]`, `r = accumulate_R(A)[1]`, `M = accumulate_M(A)` pre-computed partial normalizations
  * `maxdist = length(A)`: compute marginals only at distance `maxdist`: $|l-m|\le maxdist$
