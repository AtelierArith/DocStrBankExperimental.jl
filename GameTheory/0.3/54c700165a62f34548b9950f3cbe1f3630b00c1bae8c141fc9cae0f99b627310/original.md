```
worst_value_i(rpd, H, C, i, lp_solver=highs_optimizer_silent)
```

Given a constraint w ∈ W, this finds the worst possible payoff for agent i.

# Arguments

  * `rpd::RepGame2` : Two player repeated game.
  * `H::Matrix{Float64}` : Matrix of shape `(nH, 2)` containing the subgradients here `nH` is the number of subgradients.
  * `C::Vector{Float64}` : The array containing the hyperplane levels.
  * `i::Int` : The player of interest.
  * `lp_solver` : Linear programming solver to be used internally. Pass a `MathOptInterface.AbstractOptimizer` type (such as `HiGHS.Optimizer`) if no option is needed, or a function (such as `GameTheory.highs_optimizer_silent`) to supply options.

# Returns

  * `out::Float64` : Worst possible payoff for player i.
