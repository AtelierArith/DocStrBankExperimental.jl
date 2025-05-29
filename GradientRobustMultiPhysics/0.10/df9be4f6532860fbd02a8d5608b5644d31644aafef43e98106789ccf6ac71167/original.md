```julia
struct FEMatrix{TvM, TiM, TvG, TiG, nbrow, nbcol, nbtotal}
```

an AbstractMatrix (e.g. an ExtendableSparseMatrix) with an additional layer of several FEMatrixBlock subdivisions each carrying coefficients for their associated pair of FESpaces
