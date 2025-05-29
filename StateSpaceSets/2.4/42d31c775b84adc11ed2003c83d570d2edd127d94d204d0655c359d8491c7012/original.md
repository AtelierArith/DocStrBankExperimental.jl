```
setsofsets_distances(a₊, a₋ [, distance]) → distances
```

Calculate distances between sets of `StateSpaceSet`s. Here  `a₊, a₋` are containers of `StateSpaceSet`s, and the returned distances are dictionaries of distances. Specifically, `distances[i][j]` is the distance of the set in the `i` key of `a₊` to the `j` key of `a₋`. Distances from `a₋` to `a₊` are not computed at all, assumming symmetry in the distance function.

The `distance` can be anything valid for [`set_distance`](@ref).

Containers `a₊, a₋` can be empty but they must be concretely typed.
