```
struct LanczosIterator{F,T,O<:Orthogonalizer} <: KrylovIterator{F,T}
LanczosIterator(f, v₀, [orth::Orthogonalizer = KrylovDefaults.orth, keepvecs::Bool = true])
```

Iterator that takes a linear map `f::F` (supposed to be real symmetric or complex hermitian) and an initial vector `v₀::T` and generates an expanding `LanczosFactorization` thereof. In particular, `LanczosIterator` uses the [Lanczos iteration](https://en.wikipedia.org/wiki/Lanczos_algorithm) scheme to build a successively expanding Lanczos factorization. While `f` cannot be tested to be symmetric or hermitian directly when the linear map is encoded as a general callable object or function, it is tested whether the imaginary part of `inner(v, f(v))` is sufficiently small to be neglected.

The argument `f` can be a matrix, or a function accepting a single argument `v`, so that `f(v)` implements the action of the linear map on the vector `v`.

The optional argument `orth` specifies which [`Orthogonalizer`](@ref) to be used. The default value in [`KrylovDefaults`](@ref) is to use [`ModifiedGramSchmidtIR`](@ref), which possibly uses reorthogonalization steps. One can use to discard the old vectors that span the Krylov subspace by setting the final argument `keepvecs` to `false`. This, however, is only possible if an `orth` algorithm is used that does not rely on reorthogonalization, such as `ClassicalGramSchmidt()` or `ModifiedGramSchmidt()`. In that case, the iterator strictly uses the Lanczos three-term recurrence relation.

When iterating over an instance of `LanczosIterator`, the values being generated are instances of [`LanczosFactorization`](@ref), which can be immediately destructured into a [`basis`](@ref), [`rayleighquotient`](@ref), [`residual`](@ref), [`normres`](@ref) and [`rayleighextension`](@ref), for example as

```julia
for (V, B, r, nr, b) in LanczosIterator(f, v₀)
    # do something
    nr < tol && break # a typical stopping criterion
end
```

Note, however, that if `keepvecs=false` in `LanczosIterator`, the basis `V` cannot be extracted.

Since the iterator does not know the dimension of the underlying vector space of objects of type `T`, it keeps expanding the Krylov subspace until the residual norm `nr` falls below machine precision `eps(typeof(nr))`.

The internal state of `LanczosIterator` is the same as the return value, i.e. the corresponding `LanczosFactorization`. However, as Julia's Base iteration interface (using `Base.iterate`) requires that the state is not mutated, a `deepcopy` is produced upon every next iteration step.

Instead, you can also mutate the `KrylovFactorization` in place, using the following interface, e.g. for the same example above

```julia
iterator = LanczosIterator(f, v₀)
factorization = initialize(iterator)
while normres(factorization) > tol
    expand!(iterator, factorization)
    V, B, r, nr, b = factorization
    # do something
end
```

Here, [`initialize(::KrylovIterator)`](@ref) produces the first Krylov factorization of length 1, and `expand!(::KrylovIterator, ::KrylovFactorization)`(@ref) expands the factorization in place. See also [`initialize!(::KrylovIterator, ::KrylovFactorization)`](@ref) to initialize in an already existing factorization (most information will be discarded) and [`shrink!(::KrylovFactorization, k)`](@ref) to shrink an existing factorization down to length `k`.
