```julia
mutable struct DB <: ClusterValidityIndices.CVI
```

# 概要

デイビス-ボルダン (DB) クラスタ妥当性指標の状態情報。

# 参考文献

1. D. L. Davies と D. W. Bouldin, "クラスタ分離測定," IEEE Transaction on Pattern Analysis and Machine Intelligence, vol. 1, no. 2, pp. 224-227, 1979年2月。
2. M. Moshtaghi, J. C. Bezdek, S. M. Erfani, C. Leckie, および J. Bailey, "ストリーミングデータのためのオンラインクラスタ妥当性指標," ArXiv e-prints, 2018, arXiv:1801.02937v1 [stat.ML]. [オンライン].
3. M. Moshtaghi, J. C. Bezdek, S. M. Erfani, C. Leckie, J. Bailey, "ストリーミングデータクラスタリングのパフォーマンスモニタリングのためのオンラインクラスタ妥当性指標," Int. J. Intell. Syst., pp. 1-23, 2018年。

# フィールド

  * `label_map::Dict{Int64, Int64}`
  * `dim::Int64`
  * `n_samples::Int64`
  * `mu::Vector{Float64}`
  * `D::Matrix{Float64}`
  * `S::Vector{Float64}`
  * `params::ClusterValidityIndices.CVIElasticParams`
  * `n_clusters::Int64`
  * `criterion_value::Float64`
