```
jacobian_sparsity(f, x, sd::AbstractSparsityDetector)::AbstractMatrix{Bool}
jacobian_sparsity(f!, y, x, sd::AbstractSparsityDetector)::AbstractMatrix{Bool}
```

Use detector `sd` to construct a (typically sparse) matrix `S` describing the pattern of nonzeroes in the Jacobian of `f` (resp. `f!`) applied at `x` (resp. `(y, x)`).
