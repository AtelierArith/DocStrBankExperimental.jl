```
locate_modes!(evecs, evals=nothing; sort=true, modes=nothing)
```

For each mode (every pair of rows in `evecs`), determines the eigenvector (each  column in `evecs`) with the largest `norm` in that mode. The eigenvectors must  have dimensionality of 2n, n ∈ ℤ and be next to each other pairs. 

If `sort` is true, then the pairs of eigenvectors are sorted in-place. The eigenvalues will also be  sorted if `evals` is provided. If `sort` is false, then the `modes` vector is filled with a mapping  of the current eigenvector position to its mode (index of `modes` is the current eigenvector  position, and the element at that index in `modes` is the mode that it corresponds to). For  `sort=true`, `modes == 1:n` after calling this function.

If the mode locating is successful, `true` is returned. For unsuccessful mode locating,  `false` is returned, `modes` will contain junk, and the eigenvectors/values may be partially sorted.

Assumes the eigenvectors (and eigenvalues if provided) are already in pairs (next to  each other) starting at the first column.

### Input:

  * `evecs`  – 2n x 2n matrix of eigenvectors already in pairs
  * `evals`  – Vector of length 2n containing the eigenvalues corresponding to the eigenvectors in `evecs`
  * `sort`   – (Optional) kwarg to specify whether or not to sort the eigenvectors, default is true

### Output:

  * `ret`    – Returns true if the mode locating is successful, false if otherwise
  * `modes` – (Optional) kwarg for eigvec -> mode mapping, `length(evecs) == Int(size(evecs,1)/2)`
