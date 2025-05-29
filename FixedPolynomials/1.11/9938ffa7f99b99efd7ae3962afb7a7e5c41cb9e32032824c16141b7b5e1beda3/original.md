```
jacobian!(r::JacobianDiffResult, F, x, cfg::JacobianConfig)
```

Compute $F(x)$ and the jacobian of `F` at `x` at once using the precomputated values in `cfg` and store thre result in `r`. This is faster than computing both values separetely.

### Example

```julia
cfg = GradientConfig(g)
r = GradientDiffResult(cfg)
gradient!(r, g, x, cfg)

value(r) == g(x)
gradient(r) == gradient(g, x, cfg)
```
