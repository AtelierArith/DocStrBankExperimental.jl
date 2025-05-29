```
JuMP.result_count(model::InfiniteModel)
```

Extend `result_count` to return the number of results available to query after a  call to `optimize!`.

**Example**

```julia-repla
julia> result_count(model)
1
```
