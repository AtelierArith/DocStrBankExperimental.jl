```
TDLearner(;approximator, method, γ=1.0, α=0.01, n=0)
```

Use temporal-difference method to estimate state value or state-action value.

# Fields

  * `approximator` is `<:TabularApproximator`.
  * `γ=1.0`, discount rate.
  * `method`: only `:SARS` (Q-learning) is supported for the time being.
  * `n=0`: the number of time steps used minus 1.
