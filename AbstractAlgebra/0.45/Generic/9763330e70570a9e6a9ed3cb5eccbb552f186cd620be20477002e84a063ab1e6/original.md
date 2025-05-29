```
==(g::Perm, h::Perm)
```

Return `true` if permutations are equal, otherwise return `false`.

Permutations parametrized by different integer types are considered equal if they define the same permutation in the abstract permutation group.

# Examples

```
julia> g = Perm(Int8[2,3,1])
(1,2,3)

julia> h = perm"(3,1,2)"
(1,2,3)

julia> g == h
true
```
