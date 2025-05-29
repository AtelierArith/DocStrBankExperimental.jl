```
mutable struct SolverState
```

A state to be solved by the [`GenericSolver`](@ref). A state contains of:

  * `tree`: A partial AST
  * `active_constraints`: The local constraints that apply to this tree.   These constraints are enforced each time the tree is modified.
  * `isfeasible`: Flag to indicate if this state is still feasible.  When a propagator spots an inconsistency, this field will be set to false.  Tree manipulations and further propagations are not allowed on infeasible states
