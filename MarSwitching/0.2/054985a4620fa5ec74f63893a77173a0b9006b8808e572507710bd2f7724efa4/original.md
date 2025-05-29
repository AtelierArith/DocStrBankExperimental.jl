```
ergodic_probs(model::MSM, exog_tvtp::VecOrMat{V})
```

when applied to the non-TVTP model, returns a `k`-size Vector of ergodic probabilites of each state.      For TVTP model, returns $T \times K$ a matrix of ergodic probabilites of each state at time t.

# Arguments

  * `model::MSM`: estimated model.
  * `exog_tvtp::VecOrMat{AbstractFloat}`: optional exogenous variables for the tvtp model. If not provided, in-sample data is used.

See also [`expected_duration`](@ref).
