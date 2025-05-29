```
unmix(f°, ϕ°,    ds::DataSet)
unmix(f°, ϕ°, θ, ds::DataSet)
```

Compute the unmixed/unlensed `(f, ϕ)` from the mixed field `f°` and mixed lensing potential `ϕ°`, given the definition of the mixing matrices in `ds` evaluated at parameters `θ` (or at fiducial values if no `θ` provided). 
