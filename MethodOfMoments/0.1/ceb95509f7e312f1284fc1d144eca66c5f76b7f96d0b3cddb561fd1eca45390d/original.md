```
ClusterVCE(data, clusternames, nparam::Integer, nmoment::Integer; kwargs...)
```

Constuct an object for specifications and cache for multiway cluster-robust variance-covariance estimator. The clusters are identified by `clusternames` from `data`. The associated GMM problem involves `nparam` parameters and `nmoment` moment conditions.

# Keywords

  * `Sadj::Union{Real,Nothing}=nothing`: a factor for adjusting `S`.
  * `TF::Type=Float64`: type of the numerical values.
