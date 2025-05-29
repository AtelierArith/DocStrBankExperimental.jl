```
cartesian_size(Space::Type{<:AbstractSpace}, mesh::AbstractMesh) -> NTuple{ndims, Int}
```

Optional (only regular Cartesian grids should implement this method): Array size of Cartesian Domain.

NB: this may be different from `internal_size` if the `mesh` implements a mapping  eg to a Vector for internal model Variables.
