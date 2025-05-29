```
WhiteNoise <: AbstractNoise
```

A type for generating White Noise using `randn` - thus Gaussian noise.

The noise values are sampled from a standard normal distribution 𝒩(μ=0, σ=1). That means that ~95% of the values are between ~-2 and ~2 (with `noiselevel = 1`).
Tip: To manually create noise samples use the [`simulate_noise`](@ref) function.

# Fields

  * `noiselevel = 1` (optional): Factor that is used to scale the noise.
  * `imfilter = nothing` (optional): Use `imfilter > 0` to smooth the noise using `Image.imfilter` with a Gaussian kernel with `σ = imfilter`.

# Examples

```julia-repl
julia> noise = WhiteNoise()
WhiteNoise
  noiselevel: Int64 1
  imfilter: Nothing nothing

julia> using StableRNGs

julia> simulate_noise(StableRNG(1), noise, 3)
3-element Vector{Float64}:
 -0.5325200748641231
  0.098465514284785
  0.7528865221245234
```

See also [`PinkNoise`](@ref), [`RedNoise`](@ref), [`ExponentialNoise`](@ref), [`NoNoise`](@ref).
