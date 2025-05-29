```
mutable struct DestripingData{T <: Real, O <: Healpix.Order}
```

Structure containing the result of a destriping operation. It contains the following fields:

  * `skymap`: a `PolarizedMap` containing the maximum-likelihood map
  * `hitmap`: a map containing the weights of each pixel (this is not the hit count, as it is normalized over the value of $σ^2$ for each sample in the TOD)
  * `nobs_matrix`: an array of [`NobsMatrixelement`](@ref) objects, which can be used to determine which pixels were the most troublesome in the reconstruction of tehe I/Q/U components
  * `baselines`: the computed baselines. These must be kept as a list of `RunLengthArray` objects
  * `stopping_factors`: sequence of stopping factors, one for each iteration of the CG algorithm
  * `threshold`: upper limit on the tolerable error for the Conjugated Gradient method (optional, default is `1e-9`). See [`calc_stopping_factor`](@ref).
  * `max_iterations`: maximum number of allowed iterations for the Conjugated Gradient algorithm (optional, default is `1000`).
  * `use_preconditioner`: a Boolean flag telling whether a preconditioner should be used or not (optional, default is `true`). Usually you want this to be `true`.

The structure provides only one constructor, which accepts the following parameters:

  * `nside`: resolution of `skymap` and `hitmap`
  * `obs_list`: vector of [`Observation`](@ref); it is used to determine which pixels in the map are going to be observed
  * `runs`: list of vectors (one for each element in `obs_list`), containing the number of samples to be included in each baseline for each observation

The constructor accepts the following keywords as well:

  * `threshold` (default: `1e-9`)
  * `max_iterations` (default: 1000)
  * `use_preconditioner` (default: `true`)

The function [`destripe!`](@ref) use `DestripingData` to return the result of its computation.
