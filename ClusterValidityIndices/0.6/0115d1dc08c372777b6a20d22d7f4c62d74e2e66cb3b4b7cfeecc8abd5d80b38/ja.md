```julia
mutable struct cSIL <: ClusterValidityIndices.CVI
```

# 概要

重心ベースのシルエット (cSIL) クラスタ有効性インデックスの状態情報。

# 参考文献

1. L. E. Brito da Silva, N. M. Melton, and D. C. Wunsch II, "Incremental Cluster Validity Indices for Hard Partitions: Extensions  and  Comparative Study," ArXiv  e-prints, Feb 2019, arXiv:1902.06711v1 [cs.LG].
2. P. J. Rousseeuw, "Silhouettes: A graphical aid to the interpretation and validation of cluster analysis," Journal of Computational and Applied Mathematics, vol. 20, pp. 53-65, 1987.
3. M. Rawashdeh and A. Ralescu, "Center-wise intra-inter silhouettes," in Scalable Uncertainty Management, E. Hüllermeier, S. Link, T. Fober et al., Eds. Berlin, Heidelberg: Springer, 2012, pp. 406-419.

# フィールド

  * `label_map::Dict{Int64, Int64}`
  * `dim::Int64`
  * `n_samples::Int64`
  * `mu::Vector{Float64}`
  * `params::ClusterValidityIndices.CVIElasticParams`
  * `S::Matrix{Float64}`
  * `sil_coefs::Vector{Float64}`
  * `n_clusters::Int64`
  * `criterion_value::Float64`
