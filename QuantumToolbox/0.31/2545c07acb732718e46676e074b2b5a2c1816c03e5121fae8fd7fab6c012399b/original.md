```
isposdef(A::AbstractQuantumObject)
```

Test whether the [`AbstractQuantumObject`](@ref) is positive definite (and Hermitian) by trying to perform a Cholesky factorization of `A`.
