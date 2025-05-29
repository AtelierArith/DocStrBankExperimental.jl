```
bubblebath(
    radii::Vector{<:Real}, extent::NTuple{D,Real};
    min_distance = 0.0,
    through_boundaries = false,
    max_tries = 10000, max_fails = 100,
    verbose = true,
    rng = default_rng()
) where D
```

Generate a bath of spheres with radii `radii` in the domain `extent`.
