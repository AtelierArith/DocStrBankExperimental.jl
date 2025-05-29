```
vector_rre_backslash(x::AbstractArray, K::Integer; ϵ=0.0)
```

Applies Birkhoff vector RRE to a sequence `x_n = x[:, n]`

Arguments:

  * `x`: The sequence
  * `K`: The number of unknowns in the filter
  * `ϵ`: A regularization parameter (typically zero gives best results)

Output:

  * `c`: The learned filter
  * `sums`: The partial sums (Birkhoff averages) obtained by applying `c` to the sequence
  * `resid`: The residuals of the least-squares problem. Taking the norm gives an overall measure of the fit.
