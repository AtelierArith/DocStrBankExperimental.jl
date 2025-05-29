```
get_expect_shadow(O::MPO, shadow::ShallowShadow)
```

Compute the expectation value of an MPO operator `O` using a shallow shadow.

# Arguments:

  * `O::MPO`: The MPO operator for which the expectation value is computed.
  * `shadow::ShallowShadow`: A factorized shadow object.

# Returns:

The expectation value as a `ComplexF64` (or `Float64` if purely real).
