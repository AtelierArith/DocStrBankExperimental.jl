```
PiecewiseIncrementalCurve(initial_input::Union{Float64, Nothing}, x_coords::Vector{Float64}, slopes::Vector{Float64})
PiecewiseIncrementalCurve(input_at_zero::Union{Nothing, Float64}, initial_input::Union{Float64, Nothing}, x_coords::Vector{Float64}, slopes::Vector{Float64})
```

A piecewise linear curve specified by marginal rates (slopes) between production points. May have nonzero initial value.

# Arguments

  * `input_at_zero::Union{Nothing, Float64}`: (optional, defaults to `nothing`) cost at zero production, does NOT represent a part of the curve
  * `initial_input::Union{Float64, Nothing}`: cost at minimum production point `first(x_coords)` (NOT at zero production), defines the start of the curve
  * `x_coords::Vector{Float64}`: vector of `n` production points
  * `slopes::Vector{Float64}`: vector of `n-1` marginal rates/slopes of the curve segments between the points
