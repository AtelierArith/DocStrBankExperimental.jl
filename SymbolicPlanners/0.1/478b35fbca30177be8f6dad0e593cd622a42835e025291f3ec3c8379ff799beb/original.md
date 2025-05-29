```julia
abstract type OrderedSolution <: SymbolicPlanners.Solution
```

Abstract type for ordered planning solutions. `OrderedSolution`s should satisfy the iteration interface. Calling `get_action(sol, t::Int)` on an ordered  solution should return the intended action for step `t`.
