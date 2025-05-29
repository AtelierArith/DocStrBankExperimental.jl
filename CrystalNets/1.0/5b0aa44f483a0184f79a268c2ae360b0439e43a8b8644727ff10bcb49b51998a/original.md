```
StructureType
```

Selection mode for the crystal structure. This choice impacts the bond detection algorithm as well as the clustering algorithm used.

The choices are:

  * `Auto`: No specific structure information. Use Van der Waals radii for bond detection and `Input` as [`Clustering`](@ref), or `EachVertex` if the input does not provide residues.
  * `MOF`: Use Van der Waals radii for non-metallic atoms and larger radii for metals. Detect organic and inorganic clusters and subdivide them according to `AllNodes` and `SingleNodes` to identify underlying nets.
  * `Cluster`: similar to MOF but metallic atoms are not given a wider radius.
  * `Zeolite`: Same as `Auto` but use larger radii for metals (and metalloids) and attempt to enforce that each O atom has exactly two neighbours and that they are not O atoms.
  * `Guess`: try to identify the clusters as in `Cluster`. If it fails, fall back to `Auto`.
