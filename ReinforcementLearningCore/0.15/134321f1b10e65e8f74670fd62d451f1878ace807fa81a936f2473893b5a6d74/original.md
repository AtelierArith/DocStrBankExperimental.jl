```
discount_rewards(rewards::VectorOrMatrix, γ::Number;kwargs...)
```

Calculate the gain started from the current step with discount rate of `γ`. `rewards` can be a matrix.

# Keyword arguments

  * `dims=:`, if `rewards` is a `Matrix`, then `dims` can only be `1` or `2`.
  * `terminal=nothing`, specify if each reward follows by a terminal. `nothing` means the game is not terminated yet. If `terminal` is provided, then the size must be the same with `rewards`.
  * `init=nothing`, `init` can be used to provide the the reward estimation of the last state.

# Example
