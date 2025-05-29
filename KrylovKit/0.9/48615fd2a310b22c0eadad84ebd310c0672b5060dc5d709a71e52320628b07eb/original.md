```
struct ArnoldiIterator{F,T,O<:Orthogonalizer} <: KrylovIterator{F,T}
ArnoldiIterator(f, v₀, [orth::Orthogonalizer = KrylovDefaults.orth])
```

Iterator that takes a general linear map `f::F` and an initial vector `v₀::T` and generates an expanding `ArnoldiFactorization` thereof. In particular, `ArnoldiIterator` iterates over progressively expanding Arnoldi factorizations using the [Arnoldi iteration](https://en.wikipedia.org/wiki/Arnoldi_iteration).

The argument `f` can be a matrix, or a function accepting a single argument `v`, so that `f(v)` implements the action of the linear map on the vector `v`.

The optional argument `orth` specifies which [`Orthogonalizer`](@ref) to be used. The default value in [`KrylovDefaults`](@ref) is to use [`ModifiedGramSchmidtIR`](@ref), which possibly uses reorthogonalization steps.

When iterating over an instance of `ArnoldiIterator`, the values being generated are instances of [`ArnoldiFactorization`](@ref), which can be immediately destructured into a [`basis`](@ref), [`rayleighquotient`](@ref), [`residual`](@ref), [`normres`](@ref) and [`rayleighextension`](@ref), for example as

```julia
for (V, B, r, nr, b) in ArnoldiIterator(f, v₀)
    # do something
    nr < tol && break # a typical stopping criterion
end
```

Since the iterator does not know the dimension of the underlying vector space of objects of type `T`, it keeps expanding the Krylov subspace until the residual norm `nr` falls below machine precision `eps(typeof(nr))`.

The internal state of `ArnoldiIterator` is the same as the return value, i.e. the corresponding `ArnoldiFactorization`. However, as Julia's Base iteration interface (using `Base.iterate`) requires that the state is not mutated, a `deepcopy` is produced upon every next iteration step.

Instead, you can also mutate the `ArnoldiFactorization` in place, using the following interface, e.g. for the same example above

```julia
iterator = ArnoldiIterator(f, v₀)
factorization = initialize(iterator)
while normres(factorization) > tol
    expand!(iterator, factorization)
    V, B, r, nr, b = factorization
    # do something
end
```

Here, [`initialize(::KrylovIterator)`](@ref) produces the first Krylov factorization of length 1, and `expand!(::KrylovIterator, ::KrylovFactorization)`(@ref) expands the factorization in place. See also [`initialize!(::KrylovIterator, ::KrylovFactorization)`](@ref) to initialize in an already existing factorization (most information will be discarded) and [`shrink!(::KrylovFactorization, k)`](@ref) to shrink an existing factorization down to length `k`.
