```
destripe!(obs_list, destriping_data::DestripingData{T,O}; comm, unseen, callback) where {T <: Real, O <: Healpix.Order}
```

Apply the destriping algorithm to the TOD in `obs_list`. The result is returned in `destriping_data`, which is of type [`DestripingData`](@ref) and contains the baselines, I/Q/U maps, weight map, etc.

The parameters must satisfy the following constraints:

  * `obs_list` must be an array of `N` [`Observation`](@ref) objects;
  * `destriping_data` must be a [`DestripingData`](@ref) object. It does not need to have been initialized using [`reset_maps!`](@ref).

The optional keyword have the following meaning and default value:

  * `comm` is a MPI communicator object, or `nothing` is MPI is not used.
  * `unseen` is the value to be used for pixels in the map that have not been observed. The default is `missing`; other sensible values are `nothing` and `NaN`.
  * `callback` is either `nothing` (the default) or a function that is called before the CG algorithm starts, and then once every iteration. It can be used to monitor the progress of the destriper, or to save intermediate results in a database or a file. The function receives `destriping_data` as its parameter

The function uses Julia's `Logging` module. Therefore, you can enable the output of diagnostic messages as usual; consider the following example:

```julia
global_logger(ConsoleLogger(stderr, Debug))

# This command is going to produce a lot of output…
destripe!(...)
```
