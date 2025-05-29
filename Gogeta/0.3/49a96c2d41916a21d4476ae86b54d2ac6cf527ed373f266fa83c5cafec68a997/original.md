```
function optimize_by_sampling!(jump_model, sample_points; enhanced=true, exploitation_rate=0.67)
```

Optimizes a neural network by iteratively solving the "local" optimization problem at the sample points. The best (optimum, extremum) solution is returned.

# Arguments

  * `jump_model`: `JuMP` model containing the formulation (and desired objective function)
  * `sample_points`: A matrix where the columns are the sample inputs.

# Optional arguments

  * `enhanced`: Controls whether local optimum or only local hyperplane corner is searched for.
  * `exploitation_rate`: Controls how often the algorithm performs local search versus samples a new point.
