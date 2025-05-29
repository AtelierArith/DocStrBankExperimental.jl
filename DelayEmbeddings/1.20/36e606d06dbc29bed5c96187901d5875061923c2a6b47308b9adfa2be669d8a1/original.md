```
delay_fnn(s::AbstractVector, τ:Int, ds = 2:6; rtol=10.0, atol=2.0) → FNNs
```

Calculate the number of "false nearest neighbors" (FNNs) of the datasets created from `s` with `embed(s, d, τ) for d ∈ ds`.

## Description

Given a dataset made by `embed(s, d, τ)` the "false nearest neighbors" (FNN) are the pairs of points that are nearest to each other at dimension `d`, but are separated at dimension `d+1`. Kennel's criteria for detecting FNN are based on a threshold for the relative increment of the distance between the nearest neighbors (`rtol`, eq. 4 in[^Kennel1992]), and another threshold for the ratio between the increased distance and the "size of the attractor" (`atol`, eq. 5 in[^Kennel1992]). These thresholds are given as keyword arguments.

The returned value is a vector with the number of FNN for each `γ ∈ γs`. The optimal value for `γ` is found at the point where the number of FNN approaches zero.

See also: [`optimal_traditional_de`](@ref).
