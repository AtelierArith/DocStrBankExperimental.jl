```
multi_echo_average(
    phas::AbstractArray{<:AbstractFloat, N > 1};
    TEs::Union{Nothing, AbstractVector{<:Real}} = nothing,
    W::Union{Nothing, AbstractArray{<:AbstractFloat, N}} = nothing,
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing,
) -> typeof(similar(phas)){N-1}
```

(Weighted) Average for multi-echo data.

The weighted average is computed as

$$
\frac{\sum_{i=1}^{\#TEs} TE_i W_i phas_i}{\sum_{i=1}^{\#TEs} TE_i W_i}
$$

### Arguments

  * `phas::AbstractArray{<:AbstractFloat, N > 1}`: unwrapped multi-echo phase

### Keywords

  * `TEs::Union{Nothing, AbstractVector{<:Real}} = nothing`: echo times
  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, N}} = nothing`: weights
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`:   binary mask of region of interest

### Returns

  * `typeof(similar(phas)){N-1}`: (weighted) average of multi-echo phase
