```
StateParams{T<:Real}
```

A structure representing the parameters that govern the evolution of the state in a state-space model. This type encapsulates the fundamental components required to describe the behavior of the state process, including its initial mean, transition dynamics, noise characteristics, and the resulting covariance.

# Fields

  * N::Int   The dimensionality of the state vector. This parameter specifies the number of state variables.
  * mu::AbstractVector{T}   The initial state mean vector. It must have a length equal to N.
  * Phi::AbstractMatrix{T}   The state transition matrix, which models how the state evolves over time. This matrix should be of size N×N.
  * Omega::AbstractMatrix{T}   The state noise matrix, used to scale the impact of the stochastic noise on the state evolution. It must be of size N×N.
  * Sigma::AbstractMatrix{T}   The state covariance matrix, typically computed as Omega * Omega'. This matrix quantifies the uncertainty in the state.

# Details

The state evolution of a typical state-space model is represented by the equation:     Xₜ = mu + Phi * Xₜ₋₁ + Omega * εₜ, where εₜ represents a white noise process. This structure is a critical component in facilitating both the filtering and smoothing processes within the QuadraticKalman framework, ensuring that the model's dynamics are accurately captured and that its stability conditions can be properly validated.

This structure is also designed to integrate smoothly with automatic differentiation tools, taking advantage of Julia's type system to provide both precision and performance in numerical computations.
