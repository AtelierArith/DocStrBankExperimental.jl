```
asymmetric_qubit_3povm( θ1::Real, θ2::Real ) :: POVM
```

Constructs a general non-orthogonal 3-element `POVM`.

Inputs:

  * `θ1 ∈ (0,π/2] or [-π/2,0)`, the angle element 2 makes with $|0\rangle$ state.
  * `θ2 ∈ [-π/2,0) or (0,π/2]`, the angle element 3 makes with $|0\rangle$ state.

A `DomainError` is thrown if `θ1` and `θ2` are not in the valid ranges. Note that one angle must be positive and the other negative.
