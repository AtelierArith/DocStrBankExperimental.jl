```
    basis(fact::GKLFactorization, ::Val{which})
```

Return the list of basis vectors of a [`GKLFactorization`](@ref), where `which` should take the value `:U` or `:V` and indicates which set of basis vectors (in the domain or in the codomain of the corresponding linear map) should be returned. The return type is an `OrthonormalBasis{T}`, where `T` represents the type of the vectors used by the problem.
