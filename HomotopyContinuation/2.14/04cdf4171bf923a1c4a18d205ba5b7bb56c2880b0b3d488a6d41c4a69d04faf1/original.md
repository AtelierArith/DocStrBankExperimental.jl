```
NewtonResult
```

Result returned by [`newton`](@ref).

## Fields

  * `return_code::Symbol`: Can be `:success`, `:rejected` or `:max_iters`.
  * `x::Vector{ComplexF64}`: The last value obtained.
  * `accuracy::Float64`: Estimate of the absolute distance of `x` to a true zero.
  * `iters::Int` Number of iterations performed.
  * `contraction_ratio::Float64`: The value `|xᵢ - xᵢ₋₁| / |xᵢ₋₁ - xᵢ₋₂|`.
