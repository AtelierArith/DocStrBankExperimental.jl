```
predict(M::HeteroPCAModel, X::AbstractMatrix; λ = 0.0)
```

Column‑wise version: returns a `k × n` matrix whose *j*‑th column is `predict(M, X[:, j]; λ = λ)`.
