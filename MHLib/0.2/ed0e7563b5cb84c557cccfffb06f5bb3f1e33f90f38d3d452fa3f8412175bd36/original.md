```
Solution
```

An abstract solution to an optimization problem.

Concrete subtypes need to implement:

  * `obj_val`: objective value of solution, usually some numerical type
  * `obj_val_valid::Bool`: indicates if obj_val is valid
  * `calc_objective(::Solution)`: calculate and return objective value of solution
  * `initialize!(::Solution)`: initialize solution in some meaningful way
  * `to_maximize(::Type)`: for minimization this method must return false
  * `copy!(::Solution, ::Solution)`: make first solution a copy of the second
  * `copy(::Solution)`: return an independent copy of the solution
