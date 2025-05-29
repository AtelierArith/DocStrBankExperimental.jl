```
pair_radial_fun(pair_corr::Function, a12::T; polynomial_order::Int, mesh_size::Int)
```

Return a function `pair_radial` such that `pair_radial(r1,r2, cos(θ12))` gives the pair correlation particles at the radial distances r1 and r2, with and angle of `θ12` between them.

The function `pair_radial` is calculated from the function `pair_corr_distance`, where `pair_corr_distance(sqrt(r1^2 + r2^2 - 2r1 * r2 * cos(θ12)))` gives the pair correlation.
