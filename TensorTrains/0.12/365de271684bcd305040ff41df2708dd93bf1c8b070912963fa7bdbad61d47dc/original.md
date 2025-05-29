```
marginals(A::AbstractTensorTrain; l, r)
```

Compute the marginal distributions $p(x^l)$ at each site

### Optional arguments

  * `l = accumulate_L(A)[1]`, `r = accumulate_R(A)[1]` pre-computed partial normalizations
