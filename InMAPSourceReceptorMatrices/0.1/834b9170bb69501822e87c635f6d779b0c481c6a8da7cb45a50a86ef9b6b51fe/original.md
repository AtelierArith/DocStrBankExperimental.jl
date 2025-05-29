```
SparseSRM(emis_type, source_idxs, [layer_idxs]; threshold=0.0)
```

Make a sparse source receptor matrix, indexable via `(receptor, source, layer)`.

  * `emis_type` - The emission type for which to make the sparse matrix, ∈ ("PrimaryPM25", "SOA", "pNO3", "pSO4", "pNH4")
  * `source_idxs` - A vector of source indexes for which to add the pollution effects to the matrix
  * `layer_idxs` - A vector of layer_idxs for which to
  * `threshold=0.0` - The threshold, in units (μg / m³) / (μg / s), above which to add the value to the sparse matrix.  Adds every nonzero value by default.
