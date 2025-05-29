```
gradient!(r::GradientDiffResult, g, x, cfg::GradientConfig)
```

Compute $g(x)$ and the gradient of `g` at `x` at once using the precomputated values in `cfg` and store thre result in `r`. This is faster than calling both values separetely.

### Example

```julia
cfg = GradientConfig(g)
r = GradientDiffResult(r)
gradient!(r, g, x, cfg)

value(r) == g(x)
gradient(r) == gradient(g, x, cfg)
```
