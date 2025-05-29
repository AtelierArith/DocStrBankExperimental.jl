```julia
struct FEMatrix{TvM, TiM, TvG, TiG, nbrow, nbcol, nbtotal} <: SparseArrays.AbstractSparseArray{TvM, TiM, 2}
```

an AbstractMatrix (e.g. an ExtendableSparseMatrix) with an additional layer of several FEMatrixBlock subdivisions each carrying coefficients for their associated pair of FESpaces
