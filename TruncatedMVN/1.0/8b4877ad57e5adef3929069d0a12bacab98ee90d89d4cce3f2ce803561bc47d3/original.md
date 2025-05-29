```
 TruncatedMVNormal(mu::T, cov::S, lb::T, ub::T) where {T<:AbstractVector{<:AbstractFloat},S<:AbstractArray{<:AbstractFloat}}
```

Inner constructor of the [`TruncatedMVN.TruncatedMVNormal`](@ref) distribution.

Generates a truncated multivariate normal distribution which may be accurately sampled from using [`TruncatedMVN.sample`](@ref).

# Arguments

  * `mu::T`: D-dimensional vector of means.
  * `cov::S`: DxD-dimensional covariance matrix.
  * `lb::T`: D-dimensional vector of lower bounds.
  * `ub::T`: D-dimensional vector of upper bounds.

Bounds may be `-Inf`/`Inf`.
