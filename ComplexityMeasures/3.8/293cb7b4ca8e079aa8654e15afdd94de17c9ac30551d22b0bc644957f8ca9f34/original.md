```
LeonenkoProzantoSavani <: DifferentialInfoEstimator
LeonenkoProzantoSavani(definition = Shannon(); k = 1, w = 0)
```

The `LeonenkoProzantoSavani` estimator [LeonenkoProzantoSavani2008](@cite) computes the  [`Shannon`](@ref), [`Renyi`](@ref), or [`Tsallis`](@ref) differential [`information`](@ref) of a multi-dimensional [`StateSpaceSet`](@ref), with logarithms to the `base` specified in `definition`.

## Description

The estimator uses `k`-th nearest-neighbor searches.  `w` is the Theiler window, which determines if temporal neighbors are excluded during neighbor searches (defaults to `0`, meaning that only the point itself is excluded when searching for neighbours).

For details, see [LeonenkoProzantoSavani2008](@citet).
