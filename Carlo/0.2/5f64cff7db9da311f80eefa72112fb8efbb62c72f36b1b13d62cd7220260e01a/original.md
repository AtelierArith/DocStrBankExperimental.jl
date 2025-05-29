Holds the Carlo-internal state of the simulation and provides an interface to

  * **Random numbers**: the public field `MCContext.rng` is a random number generator (see [rng](@ref))
  * **Measurements**: see [`measure!(::MCContext, ::Symbol, ::Any)`](@ref)
  * **Simulation state**: see [`is_thermalized`](@ref)
