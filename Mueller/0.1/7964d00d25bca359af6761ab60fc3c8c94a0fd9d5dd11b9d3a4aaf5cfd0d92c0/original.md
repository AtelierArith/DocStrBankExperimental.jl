```
waveplate([T=Float64], δ=0, θ=0)
```

A generic phase retarder (waveplate) with fast axis aligned with angle `θ`, in radians, and phase delay of `δ`, in radians, along the slow axis.

# Examples

```jldoctest
julia> M = waveplate(π);

julia> M ≈ hwp()
true

julia> M = waveplate(π/2, π/4);

julia> M ≈ qwp(π/4)
true
```

# See also

[`hwp`](@ref), [`qwp`](@ref), [`mirror`](@ref)
