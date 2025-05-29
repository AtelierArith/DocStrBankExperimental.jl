```
mix(ds::DataSet; f, ϕ, [θ])
```

Compute the mixed `(f°, ϕ°)` from the unlensed field `f` and lensing potential `ϕ`, given the definition of the mixing matrices in `ds` evaluated at parameters `θ` (or at fiducial values if no `θ` provided).
