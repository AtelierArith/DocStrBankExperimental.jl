```
PiecewiseAverageCurve(initial_input::Union{Float64, Nothing}, x_coords::Vector{Float64}, slopes::Vector{Float64})
```

A piecewise linear curve specified by average rates between production points. May have nonzero initial value.

# Arguments

  * `initial_input::Union{Float64, Nothing}`: cost at minimum production point `first(x_coords)` (NOT at zero production), defines the start of the curve
  * `x_coords::Vector{Float64}`: vector of `n` production points
  * `slopes::Vector{Float64}`: vector of `n-1` average rates/slopes of the curve segments between the points
