```
condVar(m::LinearMixedModel)
```

Return the conditional variances matrices of the random effects.

The random effects are returned by `ranef` as a vector of length `k`, where `k` is the number of random effects terms.  The `i`th element is a matrix of size `vᵢ × ℓᵢ`  where `vᵢ` is the size of the vector-valued random effects for each of the `ℓᵢ` levels of the grouping factor.  Technically those values are the modes of the conditional distribution of the random effects given the observed data.

This function returns an array of `k` three dimensional arrays, where the `i`th array is of size `vᵢ × vᵢ × ℓᵢ`.  These are the diagonal blocks from the conditional variance-covariance matrix,

```
s² Λ(Λ'Z'ZΛ + I)⁻¹Λ'
```
