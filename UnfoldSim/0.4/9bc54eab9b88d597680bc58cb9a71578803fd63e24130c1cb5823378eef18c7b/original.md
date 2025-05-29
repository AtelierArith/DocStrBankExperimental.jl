```
UniformOnset <: AbstractOnset
```

Provide a Uniform Distribution for the inter-event distances (in samples).

Tip: To manually generate inter-event distance samples use the [`simulate_interonset_distances`](@ref) function.

# Fields

  * `width = 50` (optional): Width of the uniform distribution (=> the "jitter"). Since the lower bound is 0, `width` is also the upper bound.
  * `offset = 0` (optional): The minimal distance between events. The maximal distance is `offset + width`.

# Examples

```julia-repl
julia> onset_distribution = UniformOnset(width = 25, offset = 5)
UniformOnset
  width: Int64 25
  offset: Int64 5
```

See also [`LogNormalOnset`](@ref), [`NoOnset`](@ref).
