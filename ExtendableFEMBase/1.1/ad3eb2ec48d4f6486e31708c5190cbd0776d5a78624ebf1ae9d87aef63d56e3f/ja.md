```julia
struct FEMatrix{TvM, TiM, TvG, TiG, nbrow, nbcol, nbtotal} <: SparseArrays.AbstractSparseArray{TvM, TiM, 2}
```

追加のFEMatrixBlockサブディビジョンの層を持つAbstractMatrix（例：ExtendableSparseMatrix）であり、それぞれが関連するFESpacesのペアに対する係数を持っています。
