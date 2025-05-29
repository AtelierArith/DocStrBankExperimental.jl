```
assign_particles(particles::Array{P,N} where P<:AbstractParticle, symbol::Symbol, data) where N
assign_particles(particles::StructArray, symbol::Symbol, data)
```

Assign the symbol of `particles` to `data` identically.

# Examples

```jl
julia> assign_particles([Ball(uSI) for i=1:3], :Mass, 1.0u"kg")
```
