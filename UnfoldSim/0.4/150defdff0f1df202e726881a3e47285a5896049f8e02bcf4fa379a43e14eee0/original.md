```
NoNoise <: AbstractNoise
```

A type for simulations without noise; return zeros instead of noise.

Tip: To manually create noise samples use the [`simulate_noise`](@ref) function.

# Examples

```julia-repl
julia> noise = NoNoise()
NoNoise()

julia> using StableRNGs

julia> simulate_noise(StableRNG(1), noise, 3)
3-element Vector{Float64}:
 0.0
 0.0
 0.0
```

See also [`PinkNoise`](@ref), [`RedNoise`](@ref), [`ExponentialNoise`](@ref), [`WhiteNoise`](@ref).
