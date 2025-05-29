```
hessian_sparsity(f, x, sd::AbstractSparsityDetector)::AbstractMatrix{Bool}
```

Use detector `sd` to construct a (typically sparse) matrix `S` describing the pattern of nonzeroes in the Hessian of `f` applied at `x`.
