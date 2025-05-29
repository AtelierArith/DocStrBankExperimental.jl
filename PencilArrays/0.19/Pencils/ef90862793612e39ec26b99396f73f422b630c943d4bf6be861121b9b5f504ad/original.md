```
permutation(::Type{<:Pencil}) -> AbstractPermutation
permutation(p::Pencil)        -> AbstractPermutation
```

Get index permutation associated to the given pencil configuration.

Returns `NoPermutation()` if there is no associated permutation.
