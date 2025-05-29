```julia
empty!(
    lp::SpinGlassTensors.PoolOfProjectors,
    device::Symbol
) -> Union{Nothing, Dict{Int64, Union{Vector{T}, CUDA.CuVector{T}, CUDA.DenseCuVector{T}}} where T<:Integer}

```

Empty the pool of projectors associated with a specific computational device.

This function removes all projectors stored on the specified computational device, freeing up memory resources.

# Arguments:

  * `lp::PoolOfProjectors`: The `PoolOfProjectors` object containing projectors.
  * `device::Symbol`: The computational device for which projectors should be emptied (e.g., `:CPU`, `:GPU`).
