```
orthogonal_projection(V::AbstractSpace, M::T) where T <: MatElem -> AbstractSpaceMor
```

Given a space `V` and a non-degenerate subspace `W` with basis matrix `M`, return the endomorphism of `V` corresponding to the projection onto the complement of `W` in `V`.
