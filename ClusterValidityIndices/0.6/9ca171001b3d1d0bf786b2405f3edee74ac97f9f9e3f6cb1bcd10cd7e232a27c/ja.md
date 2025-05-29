```julia
mutable struct rCIP <: ClusterValidityIndices.CVI
```

# 概要

（レンイの）代表的なクロス情報ポテンシャル（rCIP）クラスタ有効性指標の状態情報。

# 参考文献

1. L. E. Brito da Silva, N. M. Melton, and D. C. Wunsch II, "Incremental Cluster Validity Indices for Hard Partitions: Extensions  and  Comparative Study," ArXiv  e-prints, Feb 2019, arXiv:1902.06711v1 [cs.LG].
2. E. Gokcay and J. C. Principe, "A new clustering evaluation function using Renyi's information potential," in Proc. Int. Conf. Acoust., Speech, Signal Process. (ICASSP), vol. 6. Jun. 2000, pp. 3490-3493.
3. E. Gokcay and J. C. Principe, "Information theoretic clustering," IEEE Trans. Pattern Anal. Mach. Intell., vol. 24, no. 2, pp. 158-171, Feb. 2002.
4. D. Araújo, A. D. Neto, and A. Martins, "Representative cross information potential clustering," Pattern Recognit. Lett., vol. 34, no. 16, pp. 2181-2191, Dec. 2013.
5. D. Araújo, A. D. Neto, and A. Martins, "Information-theoretic clustering: A representative and evolutionary approach," Expert Syst. Appl., vol. 40, no. 10, pp. 4190-4205, Aug. 2013.
6. R. O. Duda, P. E. Hart, and D. G. Stork, Pattern Classification, 2nd ed. John Wiley & Sons, 2000.

# フィールド

  * `label_map::Dict{Int64, Int64}`
  * `dim::Int64`
  * `n_samples::Int64`
  * `mu::Vector{Float64}`
  * `D::Matrix{Float64}`
  * `delta_term::Matrix{Float64}`
  * `params::ClusterValidityIndices.CVIElasticParams`
  * `sigma::ElasticArrays.ElasticArray{Float64, 3, M, V} where {M, V<:DenseVector{Float64}}`
  * `constant::Float64`
  * `n_clusters::Int64`
  * `criterion_value::Float64`
