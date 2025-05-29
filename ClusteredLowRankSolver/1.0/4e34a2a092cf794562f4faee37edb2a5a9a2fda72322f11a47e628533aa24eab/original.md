```
exact_solution(problem::Problem, primalsol::PrimalSolution, dualsol::DualSolution; transformed=false, FF = QQ, g=1, settings::RoundingSettings=RoundingSettings(), monomial_bases=nothing)
```

Compute and return an exact solution to the problem, given a primal solution, dual solution and a field `FF` with approximate generator `g`. Return `(success, exactdualsol)` if `transformed=false`, and `(success, pd_transformed_exactsolution, transformations)` if `transformed=true`.
