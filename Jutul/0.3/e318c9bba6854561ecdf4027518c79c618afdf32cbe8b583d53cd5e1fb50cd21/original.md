```
TwoPointFiniteVolumeGeometry(neighbors, areas, volumes, normals, cell_centers, face_centers)
```

Store two-point geometry information for a given list of `neighbors` specified as a `2` by `n` matrix where `n` is the number of faces such that face `i` connectes cells `N[1, i]` and `N[2, i]`.

The two-point finite-volume geometry contains the minimal set of geometry information required to compute standard finite-volume discretizations.
