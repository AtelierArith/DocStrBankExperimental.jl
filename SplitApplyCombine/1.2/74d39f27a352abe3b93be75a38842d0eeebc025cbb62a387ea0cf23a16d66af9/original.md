```
leftgroupjoin(lkey, rkey, f, comparison, left, right)
```

Creates a collection if groups labelled by `lkey(l)` where each group contains elements `f(l, r)` which satisfy `comparison(lkey(l), rkey(r))`. If there are no matches, the group is still created (with an empty collection).

This operation shares some similarities with an SQL left outer join.

### Example

```jldoctest
julia> leftgroupjoin(iseven, iseven, tuple, ==, [1,2,3,4], [0,1,2])
Dictionary{Bool,Array{Tuple{Int64,Int64},1}} with 2 entries:
  false │ Tuple{Int64,Int64}[(1, 1), (3, 1)]
  true  │ Tuple{Int64,Int64}[(2, 0), (2, 2), (4, 0), (4, 2)]
```
