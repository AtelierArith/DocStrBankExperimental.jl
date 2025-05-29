```julia
abstract type PolicySolution <: SymbolicPlanners.Solution
```

Abstract type for policy solutions. Minimally, `PolicySolution`s should implement the `get_action(sol, state::State)` method, defining the (potentially random) action to be taken at a particular `state`.
