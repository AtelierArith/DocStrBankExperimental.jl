```julia
mutable struct DB <: ClusterValidityIndices.CVI
```

# Summary

The stateful information of the Davies-Bouldin (DB) Cluster Validity Index.

# References

1. D. L. Davies and D. W. Bouldin, "A cluster separation measure," IEEE Transaction on Pattern Analysis and Machine Intelligence, vol. 1, no. 2, pp. 224-227, Feb. 1979.
2. M. Moshtaghi, J. C. Bezdek, S. M. Erfani, C. Leckie, and J. Bailey, "Online Cluster Validity Indices for Streaming Data," ArXiv e-prints, 2018, arXiv:1801.02937v1 [stat.ML]. [Online].
3. M. Moshtaghi, J. C. Bezdek, S. M. Erfani, C. Leckie, J. Bailey, "Online cluster validity indices for performance monitoring of streaming data clustering," Int. J. Intell. Syst., pp. 1-23, 2018.

# Fields

  * `label_map::Dict{Int64, Int64}`
  * `dim::Int64`
  * `n_samples::Int64`
  * `mu::Vector{Float64}`
  * `D::Matrix{Float64}`
  * `S::Vector{Float64}`
  * `params::ClusterValidityIndices.CVIElasticParams`
  * `n_clusters::Int64`
  * `criterion_value::Float64`
