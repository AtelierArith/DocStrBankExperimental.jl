```
Outgoing <: ParticleDirection
```

Concrete implementation of a [`ParticleDirection`](@ref) to indicate that a particle is *outgoing* in the context of a given process. Mostly used for dispatch.

```jldoctest
julia> using QEDbase

julia> Outgoing()
outgoing
```

!!! note "ParticleDirection Interface"
    Besides being a subtype of [`ParticleDirection`](@ref), `Outgoing` has

    ```julia
    is_incoming(::Outgoing) = false
    is_outgoing(::Outgoing) = true
    ```

