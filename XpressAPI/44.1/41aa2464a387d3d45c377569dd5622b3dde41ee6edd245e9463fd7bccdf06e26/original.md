```
XPRScrossoverlpsol(prob)::status
```

Provides a basic optimal solution for a given solution of an LP problem.

This function behaves like the crossover after the barrier algorithm.

# Arguments

  * `prob::XPRSprob`: The current problem.

# Return value

  * `status::Int32`: Pointer to an `int` where the status will be returned.

See also the documentation of the correponding function [XPRScrossoverlpsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScrossoverlpsol.html) in the C API.
