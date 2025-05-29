```
compute_receptor_emis(srm, source_idx(s), layer_idx(s), val(s)) -> receptor_emis::Vector
```

Compute the emissions at each receptor from `srm` for each source specified by `source_idx` and `layer_idx`, which correspond to `val(s)`

```
compute_receptor_emis(srm, source_emis::Matrix) -> receptor_emis::Vector
```

Compute the emissions at each receptor from `srm` for `source_emis`, a `NSR x 3` matrix containing annual average emission rates at each grid cell and layer, in units of micrograms per second.

`srm` can be any of the following types:

  * `Array{Float64, 3}` - returned by [`SRM`](@ref)
  * [`SparseSRM`](@ref)
  * `String` - pm emission type ∈ `("PrimaryPM25", "SOA", "pNO3", "pSO4", "pNH4")`
