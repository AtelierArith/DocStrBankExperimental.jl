```
abstract type InvariantCircle
```

An abstract type representing a chain of invariant circles zᵢ where zᵢ₊₁ = F(zᵢ) for i<=p and z₀ = F(zₚ₋₁). The main implementation of this type of FourierCircle, but other potential implementations of circles could exist.

Implementations should have the following functions for immediate portability:

Basic stuff

  * Initializer   `InvariantCircleImplementation(stuff)`
  * Similar   `Base.similar(z::InvariantCircle)`

Getters and Setters
 - Get number of unknown variables per circle     `get_N(z::InvariantCircle)`
 - Get period of circle     `get_p(z::InvariantCircle)`

  * Get parameters (except τ)  `get_a(z::InvariantCircle)`
  * Set parameters (except τ)  `set_a!(z::InvariantCircle, a::AbstractArray)`
  * Get rotation number τ in [0,2π)  `get_τ(z::InvariantCircle)`
  * Set τ  `set_τ!(z::InvariantCircle, τ::Number)`

Evaluation related routines

  * Evaluate the circle (see `(z::InvariantCircle)(θ, i_circle)`)   `evaluate(z::InvariantCircle, θ::AbstractVector; i_circle::Integer=1)`
  * Evaluate the derivative of the circle w.r.t. θ   `deval(z::InvariantCircle, θ::AbstractVector; i_circle::Integer=1)`
  * Get a basis Φ for z evaluated at Nθ equispaced points (requires linearity)   `get_Φ(z::InvariantCircle, Nθ::Integer; τ::Number=0.0)`
  * Evaluate the invariant circle on Φ   `function grid_eval!(x::AbstractArray, z::InvariantCircle, Φ::AbstractArray;`                       `i_circle=0)`
  * Evaluate the derivative of the invariant circle on Φ   `grid_deval!(dx::AbstractArray, z::InvariantCircle, Φ::AbstractArray;`               `i_circle=0)`

Constraints (for Newton iteration)

  * Constrain the value at 0   `fixed_θ0_constraint(z::InvariantCircle)`

Other routines (useful for continuation)

  * Get average radius   `LinearAlgebra.average_radius(z::InvariantCircle)`
  * Get the area of the invariant circle   `area(z::InvariantCircle; i_circle=1, Ns = 100)`
