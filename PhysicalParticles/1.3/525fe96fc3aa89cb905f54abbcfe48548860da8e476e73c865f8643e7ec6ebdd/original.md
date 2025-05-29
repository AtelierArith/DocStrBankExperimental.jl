```
assign_particles(particles::Array{P,N} where P<:AbstractParticle, symbol::Symbol, data::Array) where N
```

Assign the symbol of `particles` with elements in `data` one by one. `particles` and `data` must have equal length.

## Examples

```jl
julia> assign_particles([Ball(uSI) for i=1:3], :Pos, rand(PVector{Float64}, 3) * u"m")
```
