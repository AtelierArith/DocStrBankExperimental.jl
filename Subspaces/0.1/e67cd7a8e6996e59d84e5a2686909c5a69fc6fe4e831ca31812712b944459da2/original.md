```julia
dim(S::Subspaces.Subspace) -> Int64

```

Returns the linear dimension of this subspace.

```jldoctest
julia> dim(Subspace([ [1,2,3], [4,5,6] ]))
2
```
