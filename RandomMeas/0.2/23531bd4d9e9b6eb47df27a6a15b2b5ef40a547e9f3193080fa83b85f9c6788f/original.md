```
get_expect_shadow(O::MPO, shadow::AbstractShadow)
```

Compute the expectation value of an MPO operator `O` using a single shadow object.

# Arguments:

  * `O::MPO`: The MPO operator for which the expectation value is computed.
  * `shadow::AbstractShadow`: A shadow object, either dense, factorized, or shallow.

# Returns

The expectation value as a scalar.

# Example

```julia
val = get_expect_shadow(O, shadow)
```
