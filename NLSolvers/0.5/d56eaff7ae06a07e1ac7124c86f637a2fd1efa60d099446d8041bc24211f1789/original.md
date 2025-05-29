```
solve_tr_subproblem!(∇f, H, Δ, s; abstol, maxiter)
```

Args:     ∇f: The gradient     H:  The Hessian     Δ:  The trust region size, ||s|| <= Δ     s: Memory allocated for the step size, updated in place     abstol: The convergence abstol for root finding     maxiter: The maximum number of root finding iterations

Returns:     m - The numeric value of the quadratic minimization.     interior - A boolean indicating whether the solution was interior     lambda - The chosen regularizing quantity     hard_case - Whether or not it was a "hard case" as described by N&W (2006)     solved - Whether or not a solution was reached (as opposed to       terminating early due to maxiter)
