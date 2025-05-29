```julia
struct FEMatrixBlock{TvM, TiM, TvG, TiG, FETypeX, FETypeY, APTX, APTY} <: AbstractArray{TvM, 2}
```

関連するFESpacesのペアの係数を保持し、二次元のAbstractArray（getindex、setindex、size）として割り当てることができるFEMatrixのブロックです。
