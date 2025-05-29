```
isheap(v, ord::Ordering=Forward)
```

Return `true` if an array is heap-ordered according to the given order.

```jldoctest
julia> a = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> isheap(a,Base.Order.Forward)
true

julia> isheap(a,Base.Order.Reverse)
false
```
