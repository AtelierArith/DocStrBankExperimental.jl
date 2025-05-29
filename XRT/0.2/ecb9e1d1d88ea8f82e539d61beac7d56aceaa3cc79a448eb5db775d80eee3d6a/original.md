```julia
struct ToDeviceArray{T} <: XRT.AbstractSyncDirectionArray{T}
```

A data type that wraps an `Array` in order to prohibit a single synchronisation direction when calling [`XRT.sync!`](@ref) function. Can be used in functions created by [`@prepare_bitstream`](@ref) macro. Alternatively, use [`XRT.ToDeviceWrapper`](@ref) or [`XRT.FromDeviceWrapper`](@ref).
