```
multi_echo_linear_fit!(
    p::AbstractArray{<:AbstractFloat, N-1},
    phas::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    W::Union{Nothing, AbstractArray{<:AbstractFloat, N}},
    mask::Union{Nothing, AbstractArray{Bool, N-1}},
) -> p
```

(Weighted) Least squares for multi-echo data (phase offset = 0).

### Arguments

  * `p::AbstractArray{<:AbstractFloat, N-1}`: (weighted) least-squares estimate for phase
  * `phas::AbstractArray{<:AbstractFloat, N > 1}`: unwrapped multi-echo phase
  * `TEs::AbstractVector{<:Real}`: echo times
  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, N}}`:   square root of weights, e.g. reciprocal of error variance of voxel   ~> W² = 1/σ²(phas) = mag²/σ²(mag)
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}}`:   binary mask of region of interest

### Returns

  * `p`: (weighted) least-squares estimate for phase
