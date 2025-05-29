```julia
get_projector!(
    lp::SpinGlassTensors.PoolOfProjectors{T<:Integer},
    index::Int64,
    device::Symbol
) -> Union{Vector{T}, CUDA.CuVector{T}, CUDA.DenseCuVector{T}} where T<:Integer

```

TODO This is version for only one GPU

Retrieve or create a projector from the `PoolOfProjectors` associated with a specific device.

This function retrieves a projector from the `PoolOfProjectors` if it already exists. If the projector does not exist in the pool, it creates a new one and stores it for future use on the specified computational device.

# Arguments:

  * `lp::PoolOfProjectors{T}`: The `PoolOfProjectors` object containing projectors.
  * `index::Int`: The index of the projector to retrieve or create.
  * `device::Symbol`: The computational device on which the projector should be stored or retrieved (e.g., `:CPU`, `:GPU`).

# Returns:

  * `Proj{T}`: The projector of type `T` associated with the specified index and device.
