```
append(p::Permutation, ::Val{M})
```

Append `M` non-permuted dimensions to the given permutation.

# Examples

```jldoctest
julia> append(Permutation(2, 3, 1), Val(2))
Permutation(2, 3, 1, 4, 5)

julia> append(NoPermutation(), Val(2))
NoPermutation()
```
