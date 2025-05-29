```
HierarchicalCollocationPoint{N,CP,RT} <: AbstractHierarchicalCollocationPoint{N,CP,RT}
```

コレクションポイント。

# フィールド

`cpt::CP` : [`DistributedSparseGrids.CollocationPoint`](@ref) `children::SVector{N,SVector{2,HierarchicalCollocationPoint{N,CP,RT}}}` : 次元ごとに最大2つの子を持つコンテナ `parents::SVector{N,HierarchicalCollocationPoint{N,CP,RT}}` : 親のためのコンテナ  `fval::RT` : 関数値 `scaling_weight::RT` : スケーリングウェイト（関数値からcpt.coordsでのl-1レベルの補間器を引いたもの）
