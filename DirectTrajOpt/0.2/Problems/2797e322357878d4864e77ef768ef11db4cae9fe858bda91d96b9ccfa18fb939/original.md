```
mutable struct DirectTrajOptProblem <: AbstractProblem
```

Stores all the information needed to set up and solve a DirectTrajOptProblem as well as the solution after the solver terminates.

# Fields

  * `optimizer::Ipopt.Optimizer`: Ipopt optimizer object
