```
setupRegularizationProblem(A::AbstractMatrix, order::Int)
```

Precompute matrices to initialize Reguluarization Problem based on design matrix A and  zeroth, first, or second order difference operator. See Hanson (1998) and source code for details.

Example Usage

```julia
Ψ = setupRegularizationProblem(A, 0) # zeroth order problem
Ψ = setupRegularizationProblem(A, 2) # second order problem
```
