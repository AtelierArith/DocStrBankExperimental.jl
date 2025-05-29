```julia
mutable struct PS <: ClusterValidityIndices.CVI
```

# 概要

パーティション分離（PS）クラスタ妥当性指標の状態情報。

# 参考文献

1. Miin-Shen Yang and Kuo-Lung Wu, "A new validity index for fuzzy clustering," 10th IEEE International Conference on Fuzzy Systems. (Cat. No.01CH37297), Melbourne, Victoria, Australia, 2001, pp. 89-92, vol.1.
2. E. Lughofer, "Extensions of vector quantization for incremental clustering," Pattern Recognit., vol. 41, no. 3, pp. 995-1011, 2008.

# フィールド

  * `label_map::Dict{Int64, Int64}`
  * `dim::Int64`
  * `n_samples::Int64`
  * `mu::Vector{Float64}`
  * `params::ClusterValidityIndices.CVIElasticParams`
  * `D::Matrix{Float64}`
  * `n_clusters::Int64`
  * `criterion_value::Float64`
