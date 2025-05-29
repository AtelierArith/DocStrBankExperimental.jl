```
bubblebath(
    radius_pdf, ϕ_max::Real, extent::NTuple{D,Real};
    through_boundaries = false,
    max_tries = 10000, max_fails = 100,
    verbose = true
) where D
```

Generate a bath of spheres in the domain `extent`, extracting radii from `radius_pdf` trying to reach a target packing fraction `ϕ_max`. The domain is filled with spheres in order of decreasing radius.

## Keywords

  * `min_distance = 0.0`: Minimum allowed distance between spheres.   Negative values can be used to allow overlaps.
  * `through_boundaries = false`: Whether spheres can cross through the domain boundaries.
  * `max_tries = 10000`: Maximum number of insertion tries for each sphere.   When `max_tries` is reached, the sphere is discarded and the algorithm moves on   to the next one.
  * `max_fails = 100`: Maximum number of failures (i.e. discarded spheres) allowed.   Once `max_fails` is reached, the program halts.
  * `verbose = true`: Whether info logs should be printed.
  * `rng = Random.default_rng()`: Random number generator.

If a negative `min_distance` is used or `through_boundaries` is set to true, the packing fraction estimated during the generation will not correspond to the real packing fraction of the system. In these cases, `ϕ_max` has only a *semi*-quantitative value.
