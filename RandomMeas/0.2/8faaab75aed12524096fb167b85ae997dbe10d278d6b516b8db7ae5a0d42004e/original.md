```
multiply(shadow1::FactorizedShadow, shadow2::FactorizedShadow)
```

Multiply two `FactorizedShadow` objects element-wise.

# Arguments

  * `shadow1::FactorizedShadow`: The first `FactorizedShadow` object.
  * `shadow2::FactorizedShadow`: The second `FactorizedShadow` object.

# Returns

A new `FactorizedShadow` object representing the element-wise product of the two inputs.

# Notes

  * Both `shadow1` and `shadow2` must have the same number of qubits/sites.
