```julia
mutable struct WB <: ClusterValidityIndices.CVI
```

# 概要

WB-インデックス (WB) クラスタ妥当性インデックスの状態情報。

# 参考文献

1. L. E. Brito da Silva, N. M. Melton, and D. C. Wunsch II, "Incremental Cluster Validity Indices for Hard Partitions: Extensions  and  Comparative Study," ArXiv  e-prints, Feb 2019, arXiv:1902.06711v1 [cs.LG].
2. Q. Zhao, M. Xu, and P. Franti, "Sum-of-Squares Based Cluster Validity Index and Significance Analysis," in Adaptive and Natural Computing Algorithms, M. Kolehmainen, P. Toivanen, and B. Beliczynski, Eds. Berlin, Heidelberg: Springer Berlin Heidelberg, 2009, pp. 313-322.
3. Q. Zhao and P. Franti, "WB-index: A sum-of-squares based index for cluster validity," Data Knowledge Engineering, vol. 92, pp. 77-89, 2014.
4. M. Moshtaghi, J. C. Bezdek, S. M. Erfani, C. Leckie, and J. Bailey, "Online Cluster Validity Indices for Streaming Data," ArXiv e-prints, 2018, arXiv:1801.02937v1 [stat.ML].
5. M. Moshtaghi, J. C. Bezdek, S. M. Erfani, C. Leckie, J. Bailey, "Online cluster validity indices for performance monitoring of streaming data clustering," Int. J. Intell. Syst., pp. 1-23, 2018.

# フィールド

  * `label_map::Dict{Int64, Int64}`
  * `dim::Int64`
  * `n_samples::Int64`
  * `mu::Vector{Float64}`
  * `params::ClusterValidityIndices.CVIElasticParams`
  * `n_clusters::Int64`
  * `criterion_value::Float64`
