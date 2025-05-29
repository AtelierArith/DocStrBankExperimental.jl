```julia
struct FEMatrixBlock{TvM, TiM, TvG, TiG, FETypeX, FETypeY, APTX, APTY} <: AbstractArray{TvM, 2}
```

block of an FEMatrix that carries coefficients for an associated pair of FESpaces and can be assigned as an two-dimensional AbstractArray (getindex, setindex, size)
