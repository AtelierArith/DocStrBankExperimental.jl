```
PinkNoise <: AbstractNoise
```

A type for generating Pink Noise using the `SignalAnalysis.jl` implementation.

The noise values are sampled from a standard normal distribution 𝒩(μ=0, σ=1). That means that ~95% of the values are between ~-2 and ~2 (with `noiselevel = 1`).
Tip: To manually create noise samples use the [`simulate_noise`](@ref) function.

# Fields

  * `noiselevel = 1` (optional): Factor that is used to scale the noise.
  * `func = SignalAnalysis.PinkGaussian` (optional): Function that is used to create the noise samples.   This field is for internal use and should not typically be modified directly by the user.   Changes to this field may result in unexpected behavior.

# Examples

```julia-repl
julia> noise = PinkNoise(noiselevel = 3)
PinkNoise
  noiselevel: Int64 3
  func: UnionAll

julia> using StableRNGs

julia> simulate_noise(StableRNG(1), noise, 5)
5-element Vector{Float64}:
 2.578878369756878
 3.4972108606501786
 2.878568584946028
 2.2725654770788384
 3.5291669151888683
```

See also [`RedNoise`](@ref), [`WhiteNoise`](@ref), [`ExponentialNoise`](@ref), [`NoNoise`](@ref).
