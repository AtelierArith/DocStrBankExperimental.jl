```
get_hour_idxs(data, hour_idxs)
```

Converts `hour_idxs` into a usable set of indices that can index into hourly data.  `hour_idxs` can be any of the following types:

  * `Colon`
  * `Int64`
  * `AbstractVector{Int64}`
