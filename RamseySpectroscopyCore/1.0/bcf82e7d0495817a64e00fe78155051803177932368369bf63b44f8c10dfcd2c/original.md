```
pump(state_vector::StateVector, pulse::PerturbEvol) -> StateVector
```

Transform the state of a quantum system according to system's evolution in a presence of the laser pulse.

# Arguments

  * `state_vector` :   The current state vector of a quantum system.
  * `pulse` :   The laser pulse which is applied on the quantum system.

# Returns

  * `StateVector` :   Composite type instance with transformed `state` object.

# See also

  * [`StateVector`](@ref)
  * [`PerturbEvol`](@ref)

# References

  * Wikipedia: https://en.wikipedia.org/wiki/Ramsey_interferometry
