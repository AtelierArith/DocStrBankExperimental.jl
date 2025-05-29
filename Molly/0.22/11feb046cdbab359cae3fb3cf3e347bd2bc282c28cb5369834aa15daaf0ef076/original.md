```
place_diatomics(n_molecules, boundary, bond_length; min_dist=nothing,
                max_attempts=100, aligned=false, rng=Random.default_rng())
```

Generate random diatomic molecule coordinates.

Obtain coordinates for `n_molecules` diatomics in bounding box `boundary` where no two points are closer than `min_dist` and the bond length is `bond_length`, accounting for periodic boundary conditions. The keyword argument `max_attempts` determines the number of failed tries after which to stop placing atoms. The keyword argument `aligned` determines whether the bonds all point the same direction (`true`) or random directions (`false`). Can not be used if one or more dimensions has infinite boundaries.
