```
get_expect_shadow(O::MPO, shadow::DenseShadow)
```

Compute the expectation value of an MPO operator `O` using a dense shadow.

# Arguments:

  * `O::MPO`: The MPO operator for which the expectation value is computed.
  * `shadow::DenseShadow`: A dense shadow object.

# Returns:

The expectation value as a `ComplexF64` (or `Float64` if purely real).
