```
generalized_advantage_estimation(rewards::VectorOrMatrix, values::VectorOrMatrix, γ::Number, λ::Number;kwargs...)
```

Calculate the generalized advantage estimate started from the current step with discount rate of `γ` and a lambda for GAE-Lambda of 'λ'. `rewards` and 'values' can be a matrix.

# Keyword arguments

  * `dims=:`, if `rewards` is a `Matrix`, then `dims` can only be `1` or `2`.
  * `terminal=nothing`, specify if each reward follows by a terminal. `nothing` means the game is not terminated yet. If `terminal` is provided, then the size must be the same with `rewards`.

# Example
