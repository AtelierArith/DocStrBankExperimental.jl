```
rpolr(X, β, θ)
```

Generate a vector of random integers `Y` such that `P(Y[i]≤j) = g^{-1}(θ[j]-X[:,j]'β)`. `θ` has to be monotone `θ[1] ≤ ... ≤ θ[J-1]`.
