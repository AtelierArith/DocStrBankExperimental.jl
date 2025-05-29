```
durbin(r::AbstractVector)
```

Computes `y = T \ (-r)` where `T = SymmetricToeplitz(vcat(1, r[1:end-1]))`. `T` is assumed to be positive definite. `r` is of length n.
