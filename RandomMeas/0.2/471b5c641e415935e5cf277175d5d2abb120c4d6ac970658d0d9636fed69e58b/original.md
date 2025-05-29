```
multiply(shadow1::DenseShadow, shadow2::DenseShadow)
```

Compute the trace product of two dense shadows.

# Arguments

  * `shadow1::DenseShadow`: The first dense shadow.
  * `shadow2::DenseShadow`: The second dense shadow.

# Returns

A new `DenseShadow` object that represents the trace product of the two input shadows.

# Notes

  * The shadows must have the same site indices (`ξ`) and number of qubits (`N`).
