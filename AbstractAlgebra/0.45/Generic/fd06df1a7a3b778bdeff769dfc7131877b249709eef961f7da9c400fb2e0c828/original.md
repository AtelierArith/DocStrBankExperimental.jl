```
==(G::SymmetricGroup, H::SymmetricGroup)
```

Return `true` if permutation groups are equal, otherwise return `false`.

Permutation groups on the same number of letters, but parametrized by different integer types are considered different.

# Examples

```
julia> G = SymmetricGroup(UInt(5))
Permutation group over 5 elements

julia> H = SymmetricGroup(5)
Permutation group over 5 elements

julia> G == H
false
```
