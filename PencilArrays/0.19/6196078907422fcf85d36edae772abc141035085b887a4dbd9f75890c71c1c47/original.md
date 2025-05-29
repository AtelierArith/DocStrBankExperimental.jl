```
permutation(::Type{<:PencilArray})
permutation(x::PencilArray)
permutation(x::PencilArrayCollection)
```

Get index permutation associated to the given `PencilArray`.

Returns `NoPermutation()` if there is no associated permutation.
