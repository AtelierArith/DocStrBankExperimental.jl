```
weight_idw(point::Tuple, sites::AbstractMatrix; r_deg=5, nmax::Int=20, m=2)
weight_adw(point::Tuple, sites::AbstractMatrix; r_deg=5, nmax::Int=20, m=4, cdd=450)
```

# Arguments

  * `point`: Tuple of (lon, lat) coordinates
  * `sites`: Matrix of (lon, lat) coordinates
  * `r_deg`: radius in degrees
  * `nmax`: maximum number of sites
  * `m`: power of distance
