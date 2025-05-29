Simulation(PT::Type{<:AbstractParticle}; kwargs)    Simulation(ptc<:AbstractParticleContainer{N}; domainsize::NTuple{N}; kwargs...) where {N} Create a Simulation with an `N`-dimensional cuboid domain of size `domainsize`.

First argument is either a particle type `PT<:AbstractParticle{N}`, in which case the simulation is initialised with a `SimpleParticleContainer{N, PT}`, or a particle container.

# Arguments

  * `boundaries`: Specifiy the boundary conditions of the domain. Defaults to all [`Boundary`](@ref)
  * `time`: Set the initial value of the simulation clock. Defaults to `0.0`
  * `step`: Set the initial value of the timestep counter. Defaults to `0x0000000000000000`
  * `registrar`: Set the registrar. Defaults to [`SimpleRegistrar()`](@ref).
  * `rng`: Set the random number generator. Defaults to [`Random.Xoshiro`](@ref) with a randomly chosen seed
  * `threaded`: Enable multi-threaded force computation. Defaults to `false`.

!!! warning
    Multi-threaded force computation may not be supported by all particle containers

