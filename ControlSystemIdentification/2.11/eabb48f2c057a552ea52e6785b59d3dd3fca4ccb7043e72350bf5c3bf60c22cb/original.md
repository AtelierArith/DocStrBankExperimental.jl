```
schur_stab(A::AbstractMatrix{T}, ϵ = 0.01)
```

Stabilize the eigenvalues of discrete-time matrix `A` by transforming `A` to complex Schur form and projecting unstable eigenvalues 1-ϵ < λ ≤ 2 into the unit disc. Eigenvalues > 2 are set to 0.
