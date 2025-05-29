```
orthogonal_complement(V::AbstractSpace, M::T) where T <: MatElem -> T
```

Given a space `V` and a subspace `W` with basis matrix `M`, return a basis matrix of the orthogonal complement of `W` inside `V`.
