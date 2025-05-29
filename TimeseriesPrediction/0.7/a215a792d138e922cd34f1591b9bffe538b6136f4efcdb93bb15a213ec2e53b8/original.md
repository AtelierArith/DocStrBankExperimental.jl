```
temporalprediction(U, em::AbstractSpatialEmbedding, tsteps; kwargs...)
```

Perform a spatio-temporal time series prediction for `tsteps` iterations, using local weighted modeling [1] give a time series of the form `U::AbstractVector{<:AbstractArray{T, Φ}}`.

The returned data always contains the final state of `U` as starting point (total returned length is `tsteps+1`). The reconstruction process is defined by `em`. For available methods and interfaces see [`AbstractSpatialEmbedding`](@ref).

## Keyword Arguments

  * `ttype = KDTree` : Type/Constructor of tree structure. So far only tested with `KDTree`.
  * `method = AverageLocalModel(ω_safe)` : Subtype of [`AbstractLocalModel`](@ref).
  * `ntype = FixedMassNeighborhood(3)` : Subtype of `AbstractNeighborhood`.
  * `initial_ts = U` : Initial states for prediction (same type as `U`). Must have at least as many states as the maximum delay time used. Defaults to the training set `U`.
  * `progress = true` : To print progress done.

## Description

This method works similarly to [`localmodel_tsp`](@ref), by expanding the concept of delay embedding to spatially extended systems. Instead of reconstructing complete states of the system, local states are used. See [`AbstractSpatialEmbedding`](@ref) for details on the embedding. Predictions are then performed frame by frame and point py point. Once all values for a new frame are found, the frame is added to the end of the timeseries and used to generate new prediction queries for the next time step.

## Performance Notes

Be careful when choosing embedding parameters as memory usage and computation time depend strongly on the resulting embedding dimension.

## References

[1] : U. Parlitz & C. Merkwirth, [Phys. Rev. Lett. **84**, pp 1890 (2000)](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.84.1890)
