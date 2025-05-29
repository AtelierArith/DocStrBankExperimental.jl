```
isfeasible(solver::GenericSolver)
```

Returns true if no inconsistency has been detected. Used in several ways:

  * Iterators should check for infeasibility to discard infeasible states
  * After any tree manipulation with the possibility of an inconsistency (e.g. `remove_below!`, `remove_above!`, `remove!`)
  * `fix_point!` should check for infeasibility to clear its schedule and return
  * Some `GenericSolver` functions assert a feasible state for debugging purposes `@assert isfeasible(solver)`
  * Some `GenericSolver` functions have a guard that skip the function on an infeasible state: `if !isfeasible(solver) return end`
