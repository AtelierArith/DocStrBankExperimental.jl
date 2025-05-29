```
struct ProjectedConstrainedNonSmoothProblem
```

Represents a constrained nonsmooth optimisation problem whose constraints are imposed through a projection operator.  This structure provides one more member to the `NonSmoothProblem` interface: 

  * `project`: the projection operator. It takes a a vector of `dimension` Float64 and generates a vector of  `dimension` Float64. The returned point must be feasible according to the definition of the optimisation problem.

TODO: a stricter interface for projection operators? I.e. closed-form expressions or iterative solvers (they need parameters; maybe use a smooth optimisation package for this, with just constraints to be added, like `NLPModels`?). 
