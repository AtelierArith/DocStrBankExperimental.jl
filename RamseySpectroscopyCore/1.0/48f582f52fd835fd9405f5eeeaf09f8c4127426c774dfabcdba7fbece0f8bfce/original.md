```
rest!(self::StateVector, duration::FreeEvol) -> StateVector
```

Transform the state of a quantum system according to system's evolution in a presence of no perturbations.

# Arguments

  * `self` :   The current state vector of a quantum system.
  * `duration` :   The time of free evolution of the quantum system.

# Returns

  * `StateVector` :   Composite type instance with transformed `state` object.

# See also

  * [`StateVector`](@ref)
  * [`FreeEvol`](@ref)

# References

  * Wikipedia: https://en.wikipedia.org/wiki/Ramsey_interferometry
