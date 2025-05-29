```
RedNoise <: AbstractNoise
```

A type for generating Red Noise using the `SignalAnalysis.jl` implementation.

The noise values are sampled from a standard normal distribution 𝒩(μ=0, σ=1). That means that ~95% of the values are between ~-2 and ~2 (with `noiselevel = 1`).
Tip: To manually create noise samples use the [`simulate_noise`](@ref) function.

# Fields

  * `noiselevel = 1` (optional): Factor that is used to scale the noise.
  * `func = SignalAnalysis.RedGaussian` (optional): Function that is used to create the noise samples.   This field is for internal use and should not typically be modified directly by the user.   Changes to this field may result in unexpected behavior.

# Examples

```julia-repl
julia> noise = RedNoise(noiselevel = 2)
RedNoise
  noiselevel: Int64 2
  func: UnionAll

julia> using StableRNGs

julia> simulate_noise(StableRNG(2), noise, 3)
3-element Vector{Float64}:
 -0.34153942884005967
 -0.4651387715669636
 -0.4951538876376382
```

See also [`PinkNoise`](@ref), [`WhiteNoise`](@ref), [`ExponentialNoise`](@ref), [`NoNoise`](@ref).
