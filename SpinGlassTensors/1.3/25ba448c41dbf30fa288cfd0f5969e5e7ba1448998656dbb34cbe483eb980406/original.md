```julia
add_projector!(
    lp::SpinGlassTensors.PoolOfProjectors{T<:Integer},
    p::Union{Vector{T}, CUDA.CuArray{T, 1}} where T
) -> Int64

```

Add a projector to the `PoolOfProjectors` and associate it with an index.

This function adds a projector `p` to the `PoolOfProjectors`. The `PoolOfProjectors` stores projectors based on their computational device (e.g., CPU or GPU) and assigns a unique index to each projector. The index can be used to retrieve the projector later using `get_projector!`.

# Arguments:

  * `lp::PoolOfProjectors{T}`: The `PoolOfProjectors` object to which the projector should be added.
  * `p::Proj`: The projector to be added to the pool. The type of the projector `Proj` should match the type `T` specified in the `PoolOfProjectors`.

# Returns:

  * `Int`: The unique index associated with the added projector in the pool.
