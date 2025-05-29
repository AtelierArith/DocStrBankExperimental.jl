```
rayleighquotient(fact::KrylovFactorization)
```

Return the Rayleigh quotient of a [`KrylovFactorization`](@ref), i.e. the reduced matrix within the basis of the Krylov subspace. The return type is a subtype of `AbstractMatrix{<:Number}`, typically some structured matrix type.
