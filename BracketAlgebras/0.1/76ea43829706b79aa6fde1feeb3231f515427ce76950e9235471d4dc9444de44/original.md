```
point_ordering(B::BracketAlgebra)
```

Return the ordering of the n points in the bracket algebra `B`, that induces the tableaux order.

# Examples

```jldoctest
julia> point_ordering(BracketAlgebra(6,3,[2,1,3,4,5,6]))
6-element Vector{Int64}:
 2
 1
 3
 4
 5
 6
```
