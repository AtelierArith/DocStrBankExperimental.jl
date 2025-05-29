```
gradient!(u, g, x, cfg::GradientConfig [, precomputed=false])
```

Compute the gradient of `g` at `x` using the precomputated values in `cfg` and store thre result in u.

### Example

```julia
cfg = GradientConfig(g)
gradient(u, g, x, cfg)
```

With `precomputed=true` we rely on the previous intermediate results in `cfg`. Therefore the result is only correct if you previouls called `evaluate`, or `gradient` with the same `x`.
