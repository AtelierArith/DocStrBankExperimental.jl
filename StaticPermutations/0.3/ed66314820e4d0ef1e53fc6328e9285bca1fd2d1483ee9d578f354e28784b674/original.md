```
prepend(p::Permutation, ::Val{M})
```

Prepend `M` non-permuted dimensions to the given permutation.

# Examples

```jldoctest
julia> prepend(Permutation(2, 3, 1), Val(2))
Permutation(1, 2, 4, 5, 3)

julia> prepend(NoPermutation(), Val(2))
NoPermutation()
```
