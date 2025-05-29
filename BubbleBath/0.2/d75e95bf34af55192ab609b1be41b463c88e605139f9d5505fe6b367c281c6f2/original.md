```
bubblebath!(
    spheres::Vector{Sphere{D}},
    radii::Vector{<:Real}, extent::NTuple{D,Real};
    min_distance::Real = 0.0, through_boundaries = false,
    max_tries = 10000, max_fails = 100,
    verbose = true, rng = default_rng()
) where D
```

In-place version of `bubblebath`, adds new spheres to the `spheres` vector (which can be already populated).
