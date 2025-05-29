```
GeoTable(domain, values)
```

A `domain` together with a dictionary of geotable `values`. For each rank `r` (or parametric dimension) there can exist a corresponding Tables.jl table `values[r]`.

## Examples

```julia
# attach temperature and pressure to grid elements
GeoTable(CartesianGrid(10,10),
  Dict(2 => (temperature=rand(100), pressure=rand(100)))
)
```
