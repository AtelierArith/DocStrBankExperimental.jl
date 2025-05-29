```
orthonormalize(v, b::OrthonormalBasis, [x::AbstractVector,] alg::Orthogonalizer]) -> w, β, x
orthonormalize!!(v, b::OrthonormalBasis, [x::AbstractVector,] alg::Orthogonalizer]) -> w, β, x

orthonormalize(v, q, algorithm::Orthogonalizer]) -> w, β, s
orthonormalize!!(v, q, algorithm::Orthogonalizer]) -> w, β, s
```

Orthonormalize vector `v` against all the vectors in the orthonormal basis `b` using the orthogonalization algorithm `alg` of type [`Orthogonalizer`](@ref), and return the resulting vector `w` (of norm 1), its norm `β` after orthogonalizing and the overlap coefficients `x` of `v` with the basis vectors in `b`, such that `v = β * w + b * x`.

In case of `orthogonalize!`, the vector `v` is mutated in place. In both functions, storage for the overlap coefficients `x` can be provided as optional argument `x::AbstractVector` with `length(x) >= length(b)`.

One can also orthonormalize `v` against a given vector `q` (assumed to be normalized), in which case the orthonormal vector `w`, its norm `β` before normalizing and the inner product `s` between `v` and `q` are returned.

See [`orthogonalize`](@ref) if `w` does not need to be normalized.

For more information on possible orthogonalization algorithms, see [`Orthogonalizer`](@ref) and its concrete subtypes [`ClassicalGramSchmidt`](@ref), [`ModifiedGramSchmidt`](@ref), [`ClassicalGramSchmidt2`](@ref), [`ModifiedGramSchmidt2`](@ref), [`ClassicalGramSchmidtIR`](@ref) and [`ModifiedGramSchmidtIR`](@ref).
