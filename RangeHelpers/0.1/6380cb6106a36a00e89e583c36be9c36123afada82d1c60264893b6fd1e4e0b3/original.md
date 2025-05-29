```
searchsortedat(coll, x)
```

Return the index of a sorted collection `coll` whose corresponding element is closest to `x`. If `coll` is not sorted, `searchsortedat` might silently return a wrong result.

```jldoctest
julia> using RangeHelpers

julia> searchsortedat(100:100:1000, around(200))
2

julia> searchsortedat(100:100:1000, around(249))
2

julia> searchsortedat(100:100:1000, around(251))
3

julia> searchsortedat(100:100:1000, below(251))
2

julia> searchsortedat(100:100:1000, above(249))
3

julia> searchsortedat(100:100:1000, 300)
3

julia> searchsortedat(100:100:1000, 301)
ERROR: ArgumentError: coll does not contain x:
coll = 100:100:1000
x = 301
Try `searchsortedat(coll, around(x))`
```
