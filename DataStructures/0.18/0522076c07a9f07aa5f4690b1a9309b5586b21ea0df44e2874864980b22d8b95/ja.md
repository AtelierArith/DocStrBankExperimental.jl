```
isheap(v, ord::Ordering=Forward)
```

与えられた順序に従って配列がヒープ順序である場合は `true` を返します。

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
