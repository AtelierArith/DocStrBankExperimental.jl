```julia
abstract type PColorPartitions <: ExtendableGrids.AbstractGridIntegerArray1D
```

パーティションの色を記述するキータイプ。これは、与えられた色のパーティションに対して、パーティションの隣接グラフの着色に対応しており、操作（例：FEMアセンブリ）を並行して実行できます。

`grid[PColorPartitions]` は、グリッドのパーティション色（"pcolors"）を記述する整数ベクトルを返します。`p=grid[PColorPartitions]` とします。すると、すべてのパーティションは、番号 `i ∈ p[c]:p[c+1]-1` が "色" `c` を持ちます。詳細は [`pcolors`](@ref) を参照してください。
