```
boxed_correlationsum(X::AbstractStateSpaceSet, εs, r0 = maximum(εs); kwargs...) → Cs
```

Estimate the [`correlationsum`](@ref) for each size `ε ∈ εs` using an optimized algorithm that first distributes data into boxes of size `r0`, and then computes the correlation sum for each box and each neighboring box of each box. This method is much faster than [`correlationsum`](@ref), **provided that** the box size `r0` is significantly smaller than the attractor length. Good choices for `r0` are [`estimate_r0_buenoorovio`](@ref) or [`estimate_r0_theiler`](@ref).

```
boxed_correlationsum(X::AbstractStateSpaceSet; kwargs...) → εs, Cs
```

In this method the minimum inter-point distance and [`estimate_r0_buenoorovio`](@ref) of `X` are used to estimate suitable `εs` for the calculation, which are also returned.

## Keyword arguments

  * `q = 2` : The order of the correlation sum.
  * `P = 2` : The prism dimension.
  * `w = 0` : The [Theiler window](@ref).
  * `show_progress = false` : Whether to display a progress bar for the calculation.
  * `norm = Euclidean()` : Distance norm.

## Description

`C_q(ε)` is calculated for every `ε ∈ εs` and each of the boxes to then be summed up afterwards. The method of splitting the data into boxes was implemented according to [Theiler1987](@cite). `w` is the [Theiler window](@ref). `P` is the prism dimension. If `P` is unequal to the dimension of the data, only the first `P` dimensions are considered for the box distribution (this is called the prism-assisted version). By default `P` is 2, which is the version suggested by [^Bueno2007]. Alternative for `P` is the [`prismdim_theiler`](@ref). Note that only when `P = dimension(X)` the boxed version is guaranteed to be exact to the original [`correlationsum`](@ref). For any other `P`, some point pairs that should have been included may be skipped due to having smaller distance in the remaining dimensions, but larger distance in the first `P` dimensions.
