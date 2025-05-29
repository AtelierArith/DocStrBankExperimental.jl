```
LinearCurve(proportional_term::Float64)
LinearCurve(proportional_term::Float64, constant_term::Float64)
```

A linear input-output curve, representing a constant marginal rate. May have zero no-load cost (i.e., constant average rate) or not.

# Arguments

  * `proportional_term::Float64`: marginal rate
  * `constant_term::Float64`: optional, cost at zero production, defaults to `0.0`
