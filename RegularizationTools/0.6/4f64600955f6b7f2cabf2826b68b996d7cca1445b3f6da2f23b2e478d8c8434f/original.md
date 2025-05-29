```
setupRegularizationProblem(A::AbstractMatrix, L::AbstractMatrix)
```

Precompute matrices to initialize Reguluarization Problem based on design matrix and  Tikhonov smoothing matrix. See Hansen (1998, Eq. 2.35)

Example Usage

```julia
Ψ = setupRegularizationProblem(A, L) 
```
