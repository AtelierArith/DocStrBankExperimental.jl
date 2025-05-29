```
obj, pos = local_align(x, y, block, pσ=nothing, pϕ=nothing; R=nothing, T=nothing, maxevals=100)
```

Performs local alignment within the specified `block` using L-BFGS to minimize objective function `objfun` for the provided GMMs, `x` and `y`.
