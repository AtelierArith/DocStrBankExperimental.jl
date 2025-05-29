```julia
abstract type Goal <: SymbolicPlanners.Specification
```

Abstract type for goal-based specifications, which define a shortest path problem to a set of goal states. The set of goal states is typically defined by a list of terms that must hold true for the goal to be satisfied.

In the context of Markov decision processes, a goal state is a terminal state. If all actions also have positive cost (i.e. negative reward), this constitutes a stochastic shortest path problem.
