```
PhiloxNoise{N,T,R,K} <: AbstractNoise{NTuple{N,T}}
```

A noise function based on the Philox family of CBRNGs.

This is a wrapper around [`Philox2x`](@ref) and [`Philox4x`](@ref) from [`Random123`](@ref), except it guarrantees immutability.

## Examples

```jldoctest
julia> ph = Philox2x()
Philox2x{UInt64, 10}(0x4d6efe7f510f82b6, 0xd79c03fecfefaf49, 0x429f6e3e1bf363f1, 0x0000000000000000, 0x0000000000000000, 0)

julia> phn = PhiloxNoise(ph)
PhiloxNoise{2, UInt64, 10, Tuple{UInt64}}((0x429f6e3e1bf363f1,))

julia> noise(1, phn)
(0x968ebada8eb2b209, 0xd0669e24b96570df)
```
