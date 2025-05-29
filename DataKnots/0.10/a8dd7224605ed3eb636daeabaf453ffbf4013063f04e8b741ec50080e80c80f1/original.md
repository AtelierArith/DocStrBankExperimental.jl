```
 @query dataset expr param=...
```

Applies the query to a dataset with a given set of parameters.

```jldoctest
julia> @query unitknot 2x+1 x=1
┼───┼
│ 3 │
```
