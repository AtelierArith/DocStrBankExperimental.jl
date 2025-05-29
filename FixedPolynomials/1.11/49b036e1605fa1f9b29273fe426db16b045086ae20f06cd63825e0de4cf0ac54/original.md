```
GradientDiffResult(cfg::GradientConfig)
```

During the computation of $∇g(x)$ we compute nearly everything we need for the evaluation of $g(x)$. GradientDiffResult allocates memory to hold both values. This structure also signals `gradient!` to store $g(x)$ and $∇g(x)$.

### Example

```julia
cfg = GradientConfig(g, x)
r = GradientDiffResult(cfg)
gradient!(r, g, x, cfg)

value(r) == g(x)
gradient(r) == gradient(g, x, cfg)
```

```
GradientDiffResult(grad::AbstractVector)
```

Allocate the memory to hold the gradient by yourself.
