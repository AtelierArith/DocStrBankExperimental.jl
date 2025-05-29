Abstract base type for every type which might be considered a *particle* in the context of `QuantumElectrodynamics.jl`. For every (concrete) subtype of `AbstractParticle`, there are two kinds of interface functions implemented: static functions and property functions. The static functions provide information on what kind of particle it is (defaults are written in square brackets)

```julia
    is_fermion(::AbstractParticle)::Bool [= false]
    is_boson(::AbstractParticle)::Bool [= false]
    is_particle(::AbstractParticle)::Bool [= true]
    is_anti_particle(::AbstractParticle)::Bool [= false]
```

If the output of those functions differ from the defaults for a subtype of `AbstractParticle`, these functions need to be overwritten. The second type of functions define a hard interface for `AbstractParticle`:

```julia
    mass(::AbstractParticle)::Real
    charge(::AbstractParticle)::Real
```

These functions must be implemented in order to have the subtype of `AbstractParticle` work with the functionalities of `QEDprocesses.jl`.
