```
unitknot
```

The unit knot holds an empty tuple.

```jldoctest
julia> unitknot
┼──┼
│  │
```

The `unitknot` is useful for constructing queries that do not originate from another datasource.

```jldoctest
julia> unitknot["Hello"]
┼───────┼
│ Hello │
```
