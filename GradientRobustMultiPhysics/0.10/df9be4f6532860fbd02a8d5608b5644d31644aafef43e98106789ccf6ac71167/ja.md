```julia
struct FEMatrix{TvM, TiM, TvG, TiG, nbrow, nbcol, nbtotal}
```

抽象行列（例：ExtendableSparseMatrix）で、関連するFESpacesのペアに対する係数を持つ複数のFEMatrixBlockのサブディビジョンの追加レイヤーがあります。
