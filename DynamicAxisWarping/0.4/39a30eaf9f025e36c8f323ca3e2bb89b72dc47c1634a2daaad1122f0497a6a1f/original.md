```
soft_dtw_cost(args...; γ = 1, kwargs...)
```

Perform Soft DTW. This is a differentiable version of DTW. The "distance" returned by this function is quite far from a true distance and can be negative. A smaller value of `γ` makes the distance closer to the standard DTW distance.

To differentiate w.r.t. the first argument, try

```julia
using ReverseDiff
da = ReverseDiff.gradient(a->soft_dtw_cost(a,b), a)
```

Ref: "Soft-DTW: a Differentiable Loss Function for Time-Series" https://arxiv.org/pdf/1703.01541.pdf

#Arguments:

  * `args`: same as for [`dtw`](@ref)
  * `γ`: The smoothing factor. A small value means less smoothing and a result closer to [`dtw_cost`](@ref)
  * `kwargs`: same as for [`dtw`](@ref)
