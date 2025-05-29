```
Incoming <: ParticleDirection
```

Concrete implementation of a [`ParticleDirection`](@ref) to indicate that a particle is *incoming* in the context of a given process. Mostly used for dispatch.

```jldoctest
julia> using QEDbase

julia> Incoming()
incoming
```

!!! note "ParticleDirection Interface"
    Besides being a subtype of [`ParticleDirection`](@ref), `Incoming` has

    ```julia
    is_incoming(::Incoming) = true
    is_outgoing(::Incoming) = false
    ```

