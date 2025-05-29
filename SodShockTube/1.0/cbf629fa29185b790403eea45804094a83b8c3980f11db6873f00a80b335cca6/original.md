```
ShockTubeProblem
```

Contains the parameters of a shock tube problem

# Fields

`geometry::Tuple{Float64, Float64, Float64}` Contains the locations of the (left edge, right edge, initial shock location)

`left_state` Completely specified thermodynamic state of the left side of the discontinuity (NamedTuple of p, ρ, u)

`right_state` Completely specified thermodynamic state of the right side of the discontinuity (NamedTuple of p, ρ, u)

`t::Float64` The time at which the shock tube problem will be solved

`γ::Float64` The heat capacity ratio of the gas in the shock tube
