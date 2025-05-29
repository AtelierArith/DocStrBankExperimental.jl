```
abstract type AbstractLocalConstraint <: AbstractConstraint
```

Abstract type representing all local constraints. Each local constraint contains a `path` that points to a specific location in the tree at which the constraint applies.

Each local constraint should implement a [`propagate!`](@ref)-function. Inside the [`propagate!`](@ref) function, the constraint can use the following solver functions:

  * `remove!`: Elementary tree manipulation. Removes a value from a domain. (other tree manipulations are: `remove_above!`, `remove_below!`, `remove_all_but!`)
  * `deactivate!`: Prevent repropagation. Call this as soon as the constraint is satisfied.
  * `set_infeasible!`: Report a non-trivial inconsistency. Call this if the constraint can never be satisfied. An empty domain is considered a trivial inconsistency, such inconsistencies are already handled by tree manipulations.
  * `isfeasible`: Check if the current tree is still feasible. Return from the propagate function, as soon as infeasibility is detected.
