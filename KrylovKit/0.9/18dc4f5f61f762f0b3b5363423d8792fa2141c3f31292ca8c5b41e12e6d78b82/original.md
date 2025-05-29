```
orthogonalize(v, b::OrthonormalBasis, [x::AbstractVector,] alg::Orthogonalizer]) -> w, x
orthogonalize!!(v, b::OrthonormalBasis, [x::AbstractVector,] alg::Orthogonalizer]) -> w, x

orthogonalize(v, q, algorithm::Orthogonalizer]) -> w, s
orthogonalize!!(v, q, algorithm::Orthogonalizer]) -> w, s
```

Orthogonalize vector `v` against all the vectors in the orthonormal basis `b` using the orthogonalization algorithm `alg` of type [`Orthogonalizer`](@ref), and return the resulting vector `w` and the overlap coefficients `x` of `v` with the basis vectors in `b`.

In case of `orthogonalize!`, the vector `v` is mutated in place. In both functions, storage for the overlap coefficients `x` can be provided as optional argument `x::AbstractVector` with `length(x) >= length(b)`.

One can also orthogonalize `v` against a given vector `q` (assumed to be normalized), in which case the orthogonal vector `w` and the inner product `s` between `v` and `q` are returned.

Note that `w` is not normalized, see also [`orthonormalize`](@ref).

For more information on possible orthogonalization algorithms, see [`Orthogonalizer`](@ref) and its concrete subtypes [`ClassicalGramSchmidt`](@ref), [`ModifiedGramSchmidt`](@ref), [`ClassicalGramSchmidt2`](@ref), [`ModifiedGramSchmidt2`](@ref), [`ClassicalGramSchmidtIR`](@ref) and [`ModifiedGramSchmidtIR`](@ref).
