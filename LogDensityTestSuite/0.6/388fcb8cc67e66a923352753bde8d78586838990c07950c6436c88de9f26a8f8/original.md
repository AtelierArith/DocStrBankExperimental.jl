```julia
linear(A, ℓ)

```

Transform a distribution on `x` to `y = Ax`, where `A` is a conformable square matrix or a `UniformScaling` (eg `I * scalar`).

Since the log Jacobian is constant, it is dropped in the log density.
