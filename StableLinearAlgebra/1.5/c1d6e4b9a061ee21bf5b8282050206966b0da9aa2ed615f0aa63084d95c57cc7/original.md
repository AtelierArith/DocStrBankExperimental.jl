```
ldr(A::AbstractMatrix{T}) where {T}
```

Allocate an [`LDR`](@ref) factorization based on `A`, but does not calculate its [`LDR`](@ref) factorization, instead initializing the factorization to the identity matrix.
