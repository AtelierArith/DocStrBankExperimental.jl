```
evaluate(g, x, cfg::GradientConfig [, precomputed=false])
```

Evaluate `g` at `x` using the precomputated values in `cfg`. Note that this is usually signifcant faster than `evaluate(g, x)`.

### Example

```julia
cfg = GradientConfig(g)
evaluate(g, x, cfg)
```

With `precomputed=true` we rely on the previous intermediate results in `cfg`. Therefore the result is only correct if you previouls called `evaluate`, or `gradient` with the same `x`.
