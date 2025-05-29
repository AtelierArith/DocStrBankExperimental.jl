```
PerturbEvol
```

Struct for a quantum physics operator that describes evolution of quantum two-level system in a presence of some perturbation field.

# Fields

  * `operator`:   Represents operator itself in a form of a matrix.

# Arguments

  * `δ` :   The `detuning`, a measure of how far the perturbation field oscillation frequency is   off-resonance relative to the transition   (Hz).
  * `τ` :   The `duration` of Rabi/Ramsey pulse   (s).
  * `Ω₀` :   The `Rabi frequency` at which the probability amplitudes of two energy levels fluctuate   in an oscillating perturbation field   (Hz).

# Returns

  * `PerturbEvol` :   Composite type instance.

# See also

  * [`StateVector`](@ref)

# References

  * Wikipedia: https://en.wikipedia.org/wiki/Two-state*quantum*system
  * Wikipedia: https://en.wikipedia.org/wiki/Rabi_frequency
