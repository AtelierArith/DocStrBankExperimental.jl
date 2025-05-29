```
UnknownDirection <: ParticleDirection
```

Concrete implementation of a [`ParticleDirection`](@ref) to indicate that a particle has an unknown direction. This can mean that a specific direction does not make sense in the given context, that the direction is unavailable, or that it is unnecessary.

```jldoctest
julia> using QEDbase

julia> UnknownDirection()
unknown direction
```

!!! note "ParticleDirection Interface"
    Besides being a subtype of [`ParticleDirection`](@ref), `UnknownDirection` has

    ```julia
    is_incoming(::UnknownDirection) = false
    is_outgoing(::UnknownDirection) = false
    ```

