```
dominated_actions(player; tol=1e-8,
                  lp_solver=GameTheory.highs_optimizer_silent)
```

Return a vector of actions that are strictly dominated by some mixed actions.

# Arguments

  * `player::Player` : Player instance.
  * `tol::Real` : Tolerance level used in determining domination.
  * `lp_solver::Union{Type{<:MathOptInterface.AbstractOptimizer},Function}` : Linear programming solver to be used internally. Pass a `MathOptInterface.AbstractOptimizer` type (such as `HiGHS.Optimizer`) if no option is needed, or a function (such as `GameTheory.highs_optimizer_silent`) to supply options.

# Returns

  * `out::Vector{Int}` : Vector of integers representing pure actions, each of which is strictly dominated by some mixed action.
