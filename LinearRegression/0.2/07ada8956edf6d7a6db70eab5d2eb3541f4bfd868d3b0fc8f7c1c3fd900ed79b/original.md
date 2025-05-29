```
SolveQR()
```

Pass as `method` to [`linregress`](@ref) to use QR factorization to solve the linear regression system. Slower but more accurate for ill-conditioned systems than [`SolveCholesky`](@ref).
