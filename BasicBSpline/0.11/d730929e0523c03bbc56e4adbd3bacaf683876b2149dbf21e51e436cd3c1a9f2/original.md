```
@knotvector_str -> KnotVector
```

Construct a knotvector by specifying the numbers of duplicates of knots.

# Examples

```jldoctest
julia> knotvector"11111"
KnotVector([1, 2, 3, 4, 5])

julia> knotvector"123"
KnotVector([1, 2, 2, 3, 3, 3])

julia> knotvector" 2 2 2"
KnotVector([2, 2, 4, 4, 6, 6])

julia> knotvector"     1"
KnotVector([6])
```
