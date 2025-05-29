```
mul!(du, D::DerivativeOperator, u, α=true, β=false)
```

Efficient in-place version of `du = α * D * u + β * du`. Note that `du` must not be aliased with `u`.
