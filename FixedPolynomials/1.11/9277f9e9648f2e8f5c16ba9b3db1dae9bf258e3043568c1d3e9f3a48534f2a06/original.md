```
JacobianDiffResult(cfg::GradientConfig)
```

During the computation of the jacobian $J_F(x)$ we compute nearly everything we need for the evaluation of $F(x)$. `JacobianDiffResult` allocates memory to hold both values. This structure also signals `jacobian!` to store $F(x)$ and $J_F(x)$.

### Example

```julia
cfg = JacobianConfig(F, x)
r = JacobianDiffResult(cfg)
jacobian!(r, F, x, cfg)

value(r) == map(f -> f(x), F)
jacobian(r) == jacobian(F, x, cfg)
```

```
JacobianDiffResult(value::AbstractVector, jacobian::AbstractMatrix)
```

Allocate the memory to hold the value and the jacobian by yourself.
