```
bubblebath!(
    spheres::Vector{Sphere{D}},
    radius_pdf, ϕ_max::Real, extent::NTuple{D,Real};
    min_distance::Real = 0.0, through_boundaries = false,
    max_tries = 10000, max_fails = 100,
    verbose = true, rng = default_rng()
) where D
```

In-place version of `bubblebath`, adds new spheres to the `spheres` vector, which can be already populated.

Here, `ϕ_max` does **not** account for spheres that might already be present in the `spheres` vector. E.g. if `packing_fraction(spheres, extent)` is 0.2 and `ϕ_max=0.3`, then the algorithm generates new spheres for a packing fraction of 0.3, which upon insertion will (try to) add up to a total packing fraction of 0.5. To account for the pre-initialized spheres, decrease `ϕ_max` accordingly (`ϕ_max = 0.3-packing_fraction(spheres,extent)` giving 0.1 for this example).
