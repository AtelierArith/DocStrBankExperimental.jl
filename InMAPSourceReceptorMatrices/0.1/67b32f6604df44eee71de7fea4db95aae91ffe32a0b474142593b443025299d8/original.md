```
SparseSRM(srm, source_idxs, [layer_idxs]; threshold=0.0)
```

Make a sparse source receptor matrix from an SRM (`Array{Float32, 3}`).

  * `emis_type` - The emission type for which to make the sparse matrix.
  * `source_idxs` - A vector of source indexes for which to add the pollution effects to the matrix
  * `layer_idxs` - A vector of layer_idxs for which to
  * `threshold=0.0` - The threshold, in units (μg / m³) / (μg / s), above which to add the value to the sparse matrix.  Adds every nonzero value by default.
