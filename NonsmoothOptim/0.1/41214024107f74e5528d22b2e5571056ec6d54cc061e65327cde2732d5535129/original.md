```
abstract type ConstrainedNonSmoothProblem <: NonSmoothProblem
```

Represents a constrained nonsmooth optimisation problem. It does not imply any new properties with respect to a  `NonSmoothProblem`, because they might heavily depend on the kind of optimisation solver that is used (indicator function, polytope, projection operator, proximale operator, etc.)
