```julia
mutable struct FAM <: AdaptiveResonance.ARTMAP
```

# 概要

Fuzzy ARTMAP 構造体。

モジュールオプションについては、[`AdaptiveResonance.opts_FAM`](@ref)を参照してください。

# 参考文献

1. G. A. Carpenter, S. Grossberg, N. Markuzon, J. H. Reynolds, and D. B. Rosen, “Fuzzy ARTMAP: A Neural Network Architecture for Incremental Supervised Learning of Analog Multidimensional Maps,” IEEE Trans. Neural Networks, vol. 3, no. 5, pp. 698-713, 1992, doi: 10.1109/72.159059.

# フィールド

  * `opts::AdaptiveResonance.opts_FAM`: Fuzzy ARTMAP オプション構造体。
  * `config::AdaptiveResonance.DataConfig`: データ構成構造体。
  * `W::ElasticArrays.ElasticMatrix{Float64, V} where V<:DenseVector{Float64}`: カテゴリ重み行列。
  * `labels::Vector{Int64}`: 各 F2 ノードに対応するラベルの増分リスト、自己指定または監視されたもの。
  * `n_categories::Int64`: カテゴリ重みの数 (F2 ノード)。
  * `epoch::Int64`: 現在のトレーニングエポック。
