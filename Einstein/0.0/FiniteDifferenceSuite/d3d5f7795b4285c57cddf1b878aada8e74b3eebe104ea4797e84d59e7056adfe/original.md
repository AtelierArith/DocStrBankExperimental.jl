```
fdm_extrapolation_weights(extrapolation_order::Int, direction::Symbol)
```

Generate weights for left or right extrapolation.

# Arguments

  * `extrapolation_order::Int`: Order of extrapolation
  * `direction::Symbol`: Direction of extrapolation (:left or :right)

# Returns

Vector of Integer coefficients for the extrapolation weights.
