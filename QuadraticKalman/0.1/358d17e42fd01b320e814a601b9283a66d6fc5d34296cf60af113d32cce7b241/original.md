```
MeasParams{T<:Real}
```

A container for the measurement equation parameters in a quadratic state-space model.

This structure holds all measurement-related parameters essential for specifying the measurement equation:

Yₜ = A + B * Xₜ + α * Yₜ₋₁ + ∑₍ᵢ₌₁₎ᴹ (Xₜ' * Cᵢ * Xₜ) + noise

where:   • M: The number of measurement variables.   • A: A vector of intercept terms (length M).   • B: An M×N matrix mapping the state vector (of dimension N) to the measurement space.   • C: A vector of M matrices, each of size N×N, representing quadratic measurement parameters.   • D: An M×M matrix scaling the measurement noise.   • α: An M×M matrix capturing the autoregressive component in the measurement equation.   • V: An auxiliary M×M matrix computed as V = D * D', representing the covariance structure of the measurement noise.

All fields should be provided as concrete matrices or vectors (or will be derived from UniformScaling objects as needed), ensuring consistency and compatibility with downstream filtering and smoothing routines. The use of the @with_kw macro facilitates clear initialization and automatic field assignment.
