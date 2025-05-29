```
calculate_samples(m::Int, delta::Float64, alph::Float64)::Int
```

Generate enough samples to satisfy the error bound with respect to the tensorized Chebyshev polynomial basis.

# Arguments

  * `m::Int`: Dimension of the polynomial space.
  * `delta::Float64`: Relative error bound.
  * `alph::Float64`: Probability, confidence level.

# Returns

  * The required number of samples.

# Example

```julia
calculate_samples(10, 0.1, 0.05)
```
