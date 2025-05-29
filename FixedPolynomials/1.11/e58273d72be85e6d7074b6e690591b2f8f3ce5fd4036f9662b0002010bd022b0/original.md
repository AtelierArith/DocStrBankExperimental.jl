```
evaluate(F, x, cfg::JacobianConfig [, precomputed=false])
```

Evaluate the system `F` at `x` using the precomputated values in `cfg`. Note that this is usually signifcant faster than `map(f -> evaluate(f, x), F)`. The return vector is constructed using `similar(x, T)`.

### Example

```julia
cfg = JacobianConfig(F)
evaluate(F, x, cfg)
```

With `precomputed=true` we rely on the previous intermediate results in `cfg`. Therefore the result is only correct if you previouls called `evaluate`, or `jacobian` with the same `x`.
