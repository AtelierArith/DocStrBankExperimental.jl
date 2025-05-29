```
SolveCholesky()
```

Pass as `method` to [`linregress`](@ref) to use Cholesky factorization to solve the linear regression system. Faster but less accurate for ill-conditioned systems than [`SolveQR`](@ref).
