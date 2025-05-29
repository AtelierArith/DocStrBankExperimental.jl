```
levinson(r::AbstractVector, b::AbstractVector)
```

Solves `x = T \ b` where `T = SymmetricToeplitz(vcat(1, r))`, i.e. `T_{ij} = r[abs(i-j)]` where by assumption `r[0] = 1` and `T` is positive definite.
