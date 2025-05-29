```
isidentity(p::Permutation)
```

Returns `true` if `p` is an identity permutation, i.e. if it is equivalent to `(1, 2, 3, ...)`.

```jldoctest
julia> isidentity(Permutation(1, 2, 3))
true

julia> isidentity(Permutation(1, 3, 2))
false

julia> isidentity(NoPermutation())
true
```
