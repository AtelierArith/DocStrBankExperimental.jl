```
ColorfieldSurfaceNormal(; boundary_contact_threshold=0.1, interface_threshold=0.01,
                          ideal_density_threshold=0.0)
```

Color field based computation of the interface normals.

# Keyword Arguments

  * `boundary_contact_threshold=0.1`: If this threshold is reached the fluid is assumed to be in contact with the boundary.
  * `interface_threshold=0.01`:       Threshold for normals to be removed as being invalid.
  * `ideal_density_threshold=0.0`:    Assume particles are inside if they are above this threshold, which is relative to the `ideal_neighbor_count`.
