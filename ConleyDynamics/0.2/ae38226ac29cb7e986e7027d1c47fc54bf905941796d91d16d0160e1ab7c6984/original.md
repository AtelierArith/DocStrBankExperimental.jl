```
lefschetz_information(lc::LefschetzComplex)
```

Extract basic information about a Lefschetz complex.

The input argument `lc` contains the Lefschetz complex. The function returns the information in the form of a `Dict{String,Any}`. You can use the command `keys` to see the keyset of the return dictionary:

  * `"Dimension"`: Dimension of the Lefschetz complex
  * `"Coefficient field"`: Underlying coefficient field
  * `"Euler characteristic"`: Euler characteristic of the complex
  * `"Homology"`: Betti numbers of the Lefschetz complex
  * `"Boundary sparsity"`: Sparsity percentage of the boundary matrix
  * `"Number of cells"`: Total number of cells in the complex
  * `"Cell counts by dim"`: Cell counts by dimension

In the last case, the dictionary entry is a vector of pairs `(dimension, cell count)`.
