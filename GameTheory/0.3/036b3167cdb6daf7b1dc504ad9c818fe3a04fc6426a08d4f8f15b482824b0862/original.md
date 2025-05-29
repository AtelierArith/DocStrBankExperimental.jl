```
is_dominated(player, action; tol=1e-8,
             lp_solver=GameTheory.highs_optimizer_silent)
```

Determine whether `action` is strictly dominated by some mixed action.

# Arguments

  * `player::Player` : Player instance.
  * `action::PureAction` : Integer representing a pure action.
  * `tol::Real` : Tolerance level used in determining domination.
  * `lp_solver` : Linear programming solver to be used internally. Pass a `MathOptInterface.AbstractOptimizer` type (such as `HiGHS.Optimizer`) if no option is needed, or a function (such as `GameTheory.highs_optimizer_silent`) to supply options.

# Returns

  * `::Bool` : True if `action` is strictly dominated by some mixed action; false otherwise.
