```
sign(g::Perm)
```

Return the sign of a permutation.

`sign` returns $1$ if `g` is even and $-1$ if `g` is odd. `sign` represents the homomorphism from the permutation group to the unit group of $\mathbb{Z}$ whose kernel is the alternating group.

# Examples

```jldoctest
julia> g = Perm([3,4,1,2,5])
(1,3)(2,4)

julia> sign(g)
1

julia> g = Perm([3,4,5,2,1,6])
(1,3,5)(2,4)

julia> sign(g)
-1
```
