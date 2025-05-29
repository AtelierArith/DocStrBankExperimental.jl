```
trace(shadow::FactorizedShadow)
```

Compute the trace of a `FactorizedShadow` object.

# Arguments

  * `shadow::FactorizedShadow`: The `FactorizedShadow` object whose trace is to be computed.

# Returns

The trace of the shadow as a `Float64` or `ComplexF64`.

# Notes

  * The function computes the product of the traces of individual tensors in the factorized shadow.
