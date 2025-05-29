```
multi_echo_linear_fit!(
    p::AbstractArray{<:AbstractFloat, N-1},
    p0::AbstractArray{<:AbstractFloat, N-1},
    phas::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    W::Union{Nothing, AbstractArray{<:AbstractFloat, N}},
    mask::Union{Nothing, AbstractArray{Bool, N-1}},
) -> (p, p0)
```

(Weighted) Least squares for multi-echo data (estimate phase offset).

### Arguments

  * `p::AbstractArray{<:AbstractFloat, N-1}`: (weighted) least-squares estimate for phase
  * `p0::AbstractArray{<:AbstractFloat, N-1}`: (weighted) least-squares estimate for phase offset
  * `phas::AbstractArray{<:AbstractFloat, N > 1}`: unwrapped multi-echo phase
  * `TEs::AbstractVector{<:Real}`: echo times
  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, N}}`:   square root of weights, e.g. reciprocal of error variance of voxel   ~> W² = 1/σ²(phas) = mag²/σ²(mag)
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}}`:   binary mask of region of interest

### Returns

  * `p`: (weighted) least-squares estimate for phase
  * `p0`: (weighted) least-squares estimate for phase offset
