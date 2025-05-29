```
Quantum2Level
```

Class that describes the quantum two-level system via parameters of that system.

# Fields

  * `mass` :   Represents a value of the quantum system's mass   (kg).
  * `temperature` :   Represents a value of the quantum system's temperature   (K).
  * `relax_sp` :   Represents a value of the spontaneous emission frequency in quantum system and   considered to be constant in this model, referred to as `γ₀` in other documentation   and below   (Hz).
  * `relax_opt` :   Represents a value of the optical emission frequency of optical transitions in quantum   system and considered to be constant in this model   (units of `γ₀`).
  * `dimmless_velocity` :   Represents a value of the quantum system's most probable velocity in   dimensionless units.

# Arguments

  * `M`, `T`, `γ₀`, `γₒₚₜ` :   Refer to fields' description.
  * `light` :   Light source which is used to interact with the quantum two-level system.

# Returns

  * `Quantum2Level` :   Composite type instance.

# See also

  * [`LightSource`](@ref)

# References

  * Wikipedia: https://en.wikipedia.org/wiki/Density_matrix
  * Wikipedia: https://en.wikipedia.org/wiki/Spontaneous_emission
