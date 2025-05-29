```
parent(a)
```

Return parent object of given element $a$.

# Examples

```jldoctest
julia> G = SymmetricGroup(5); g = Perm([3,4,5,2,1])
(1,3,5)(2,4)

julia> parent(g) == G
true

julia> S, x = laurent_series_ring(ZZ, 3, :x)
(Laurent series ring in x over integers, x + O(x^4))

julia> parent(x) == S
true
```
