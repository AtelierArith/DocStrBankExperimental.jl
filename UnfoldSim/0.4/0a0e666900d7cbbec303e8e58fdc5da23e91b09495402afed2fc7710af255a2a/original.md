```
ExponentialNoise <: AbstractNoise
```

Type for generating noise with exponential decay in AR spectrum.

Tip: To manually create noise samples use the [`simulate_noise`](@ref) function.

!!! warning
    With the current implementation we try to get exponential decay over the whole autoregressive (AR) spectrum, which is N samples (the total number of samples in the signal) long. This involves the inversion of a Cholesky matrix of size NxN matrix, which will need lots of RAM for non-trivial problems.


# Fields

  * `noiselevel = 1` (optional): Factor that is used to scale the noise.
  * `ν = 1.5` (optional): Exponential factor of AR decay "nu".

# Examples

```julia-repl
julia> noise = ExponentialNoise()
ExponentialNoise
  noiselevel: Int64 1
  ν: Float64 1.5

julia> using StableRNGs

julia> simulate_noise(StableRNG(1), noise, 5)
5-element Vector{Float64}:
  -5.325200748641231
  -3.437402125380177
   2.7852625669058884
  -1.5381022393382109
 -14.818799857226612
```

See also [`PinkNoise`](@ref), [`RedNoise`](@ref), [`NoNoise`](@ref), [`WhiteNoise`](@ref).
