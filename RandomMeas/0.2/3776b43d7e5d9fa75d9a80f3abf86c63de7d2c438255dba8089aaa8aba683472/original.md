```
trace(shadow::DenseShadow)
```

Compute the trace of a `DenseShadow` object.

# Arguments

  * `shadow::DenseShadow`: The `DenseShadow` object whose trace is to be computed.

# Returns

The trace of the shadow as a `Float64` or `ComplexF64`.

# Notes

  * The function contracts the `ξ` and `ξ'` indices of the shadow's ITensor.
