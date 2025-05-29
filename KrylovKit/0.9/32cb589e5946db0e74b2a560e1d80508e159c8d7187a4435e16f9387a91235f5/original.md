```
    basis(fact::KrylovFactorization)
```

Return the list of basis vectors of a [`KrylovFactorization`](@ref), which span the Krylov subspace. The return type is a subtype of `Basis{T}`, where `T` represents the type of the vectors used by the problem.
