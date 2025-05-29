```
cov(Dᵩ::AbstractStructFunc, S, σ=0; pack=false) -> Cᵩ
```

yields the covariance of a random field whose structure function is `Dᵩ` over an support defined by `S` and whose piston mode has a standard deviation of `σ`.

The range of indices to consider for the random field is the same as that of `S` unless keyword `pack` is true, in which case only the indices inside the support `S` are considered.

The result is a flattened `n×n` covariance matrix with `n = length(S)` if `pack` is false, or with `n` the number of non-zeros in the support `S` if `pack` is true.

The implemented method is described in the notes accompanying this package.
