```
ReachabilitySolver{S} <: Solver
```

Solves reachability and constrained reachability problems in MDPs and POMDPs. It returns the policy that maximizes the probability of reaching a given set of states. It takes as input the set of states to reach and the set of states to avoid, as well as the underlying solver. Any solver from POMDPs.jl are supported.

# Fields

The field are specified as keyword arguments to the solver.

  * `reach::Set{S}` the set of states to reach
  * `avoid::Set{S}` the set of states to avoid
  * `solver::Solver` the underlying solver to use (default is `ValueIterationSolver`)
