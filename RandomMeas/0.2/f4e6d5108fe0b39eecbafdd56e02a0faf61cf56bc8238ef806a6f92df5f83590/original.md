```
get_expect_shadow(O::MPO, shadow::FactorizedShadow)
```

Compute the expectation value of an MPO operator `O` using a factorized shadow.

# Arguments:

  * `O::MPO`: The MPO operator for which the expectation value is computed.
  * `shadow::FactorizedShadow`: A factorized shadow object.

# Returns:

The expectation value as a `ComplexF64` (or `Float64` if purely real).
