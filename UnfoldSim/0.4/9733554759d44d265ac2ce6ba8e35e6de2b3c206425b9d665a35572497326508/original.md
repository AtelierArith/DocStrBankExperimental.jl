```
simulate_noise(rng, t::AbstractNoise, n::Int)
```

Generate noise samples of the given type `t`.

For details, see the documentation of the individual noise types. Use `subtypes(AbstractNoise)` for a list of the implemented noise types.

# Arguments

  * `rng::AbstractRNG`: Random number generator (RNG) to make the process reproducible.
  * `t::AbstractNoise`: Instance of a noise type e.g. `PinkNoise()`.
  * `n::Int`: The number of noise samples that should be generated.

# Returns

  * `Vector`: Vector of length `n` containing the noise samples.

# Examples

```julia-repl
# Here we use White Noise as an example but it works in the same way for the other noise types.
julia> noise = WhiteNoise()
WhiteNoise
  noiselevel: Int64 1
  imfilter: Int64 0

julia> using StableRNGs

julia> simulate_noise(StableRNG(1), noise, 3)
3-element Vector{Float64}:
 -0.5325200748641231
  0.098465514284785
  0.7528865221245234
```
