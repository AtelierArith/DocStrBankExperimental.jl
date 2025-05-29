```
expected_duration(model::MSM, exog_tvtp::VecOrMat{AbstractFloat})
```

For non-TVTP model, returns Vector of expected duration of each state. For TVTP model, returns a matrix of expected duration of each state at timt t.    

formula: `1 / (1 - P[i,i])` or for TVTP - `1 / (1 - P[i,i, t])`

# Arguments

  * `model::MSM`: estimated model.
  * `exog_tvtp::VecOrMat{AbstractFloat}`: optional exogenous variables for the tvtp model. If not provided, in-sample data is used.

See also [`ergodic_probs`](@ref).
