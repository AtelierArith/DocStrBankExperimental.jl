```
one(::S) where {S<:ElementarySpace} -> ProductSpace{S, 0}
one(::ProductSpace{S}) where {S<:ElementarySpace} -> ProductSpace{S, 0}
```

Return a tensor product of zero spaces of type `S`, i.e. this is the unit object under the tensor product operation, such that `V ⊗ one(V) == V`.
