```julia
MinimizationProblem(objective, lower_bounds, upper_bounds)

```

Define a minimization problem.

  * `objective` is a function that maps `ℝᴺ` vectors to real numbers. It should accept all  `AbstractVector`s of length `N`.
  * `lower_bounds` and `upper_bounds` define the bounds, and their lengths implicitly define the dimension `N`.

The fields of the result should be accessible with the names above.
