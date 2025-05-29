```
place_atoms(n_atoms, boundary; min_dist=nothing, max_attempts=100, rng=Random.default_rng())
```

Generate random coordinates.

Obtain `n_atoms` coordinates in bounding box `boundary` where no two points are closer than `min_dist`, accounting for periodic boundary conditions. The keyword argument `max_attempts` determines the number of failed tries after which to stop placing atoms. Can not be used if one or more dimensions has infinite boundaries.
