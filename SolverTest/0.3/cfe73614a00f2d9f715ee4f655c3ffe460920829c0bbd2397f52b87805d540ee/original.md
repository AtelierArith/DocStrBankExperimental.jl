```
multiprecision_nlp(solver, problem_type; precisions=[Float16, …, BigFloat])
```

Test that `solver` solves a problem of type `problem_type` on various `precisions`. The `problem_type` can be

  * :unc
  * :bnd
  * :equ
  * :ineq
  * :eqnbnd
  * :gen
