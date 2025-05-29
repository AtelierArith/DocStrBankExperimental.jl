```
Map_Cache
```

Map cache struct, mutable.

| **Field**        | **Type**                  | **Description**                                                                             |
|:---------------- |:------------------------- |:------------------------------------------------------------------------------------------- |
| `maps`           | Vector{`MapS`{`Float64`}} | vector of `MapS` scalar magnetic anomaly map structs                                        |
| `map_sort_ind`   | Vector{`Int64`}           | `maps` indices sorted by altitude                                                           |
| `fallback`       | `MapS`{`Float64`}         | fallback `MapS` scalar magnetic anomaly map struct                                          |
| `map_cache`      | Dict                      | `maps`     cache of scalar map interpolation functions (`f(lat,lon)`) at multiple altitudes |
| `fallback_cache` | Dict                      | `fallback` cache of scalar map interpolation functions (`f(lat,lon)`) at multiple altitudes |
| `dz`             | Real                      | step size between map altitude levels [m]                                                   |
