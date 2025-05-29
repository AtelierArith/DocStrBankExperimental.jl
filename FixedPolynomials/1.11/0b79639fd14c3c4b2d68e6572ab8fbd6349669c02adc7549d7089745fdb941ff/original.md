```
jacobian(u, F, x, cfg::JacobianConfig [, precomputed=false])
```

Evaluate the jacobian of `F` at `x` using the precomputated values in `cfg`. The return matrix is constructed using `similar(x, T, m, n)`.

### Example

```julia
cfg = JacobianConfig(F)
jacobian(F, x, cfg)
```

With `precomputed=true` we rely on the previous intermediate results in `cfg`. Therefore the result is only correct if you previouls called `evaluate`, or `jacobian` with the same `x`.
