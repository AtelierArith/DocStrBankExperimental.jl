```
struct GKLIterator{F,TU,O<:Orthogonalizer}
GKLIterator(f, u₀, [orth::Orthogonalizer = KrylovDefaults.orth, keepvecs::Bool = true])
```

Iterator that takes a general linear map `f::F` and an initial vector `u₀::TU` and generates an expanding `GKLFactorization` thereof. In particular, `GKLIterator` implements the [Golub-Kahan-Lanczos bidiagonalization procedure](http://www.netlib.org/utk/people/JackDongarra/etemplates/node198.html). Note, however, that this implementation starts from a vector `u₀` in the codomain of the linear map `f`, which will end up (after normalisation) as the first column of `U`.

The argument `f` can be a matrix, a tuple of two functions where the first represents the normal action and the second the adjoint action, or a function accepting two arguments, where the first argument is the vector to which the linear map needs to be applied, and the second argument is either `Val(false)` for the normal action and `Val(true)` for the adjoint action. Note that the flag is thus a `Val` type to allow for type stability in cases where the vectors in the domain and the codomain of the linear map have a different type.

The optional argument `orth` specifies which [`Orthogonalizer`](@ref) to be used. The default value in [`KrylovDefaults`](@ref) is to use [`ModifiedGramSchmidtIR`](@ref), which possibly uses reorthogonalization steps.

When iterating over an instance of `GKLIterator`, the values being generated are instances `fact` of [`GKLFactorization`](@ref), which can be immediately destructured into a [`basis(fact, Val(:U))`](@ref), [`basis(fact, Val(:V))`](@ref), [`rayleighquotient`](@ref), [`residual`](@ref), [`normres`](@ref) and [`rayleighextension`](@ref), for example as

```julia
for (U, V, B, r, nr, b) in GKLIterator(f, u₀)
    # do something
    nr < tol && break # a typical stopping criterion
end
```

Since the iterator does not know the dimension of the underlying vector space of objects of type `T`, it keeps expanding the Krylov subspace until the residual norm `nr` falls below machine precision `eps(typeof(nr))`.

The internal state of `GKLIterator` is the same as the return value, i.e. the corresponding `GKLFactorization`. However, as Julia's Base iteration interface (using `Base.iterate`) requires that the state is not mutated, a `deepcopy` is produced upon every next iteration step.

Instead, you can also mutate the `GKLFactorization` in place, using the following interface, e.g. for the same example above

```julia
iterator = GKLIterator(f, u₀)
factorization = initialize(iterator)
while normres(factorization) > tol
    expand!(iterator, factorization)
    U, V, B, r, nr, b = factorization
    # do something
end
```

Here, [`initialize(::GKLIterator)`](@ref) produces the first GKL factorization of length 1, and `expand!(::GKLIterator, ::GKLFactorization)`(@ref) expands the factorization in place. See also [`initialize!(::GKLIterator, ::GKLFactorization)`](@ref) to initialize in an already existing factorization (most information will be discarded) and [`shrink!(::GKLIterator, k)`](@ref) to shrink an existing factorization down to length `k`.
