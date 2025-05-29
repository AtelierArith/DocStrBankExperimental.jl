```
inner(M::FixedRankMatrices, p::SVDMPoint, X::UMVTangentVector, Y::UMVTangentVector)
```

Compute the inner product of `X` and `Y` in the tangent space of `p` on the [`FixedRankMatrices`](@ref) `M`, which is inherited from the embedding, i.e. can be computed using `dot` on the elements (`U`, `Vt`, `M`) of `X` and `Y`.
