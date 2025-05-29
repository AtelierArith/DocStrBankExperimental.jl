This specific Newton-Krylov method first tries to converge to a solution `sol0` close the guess `x0`. It then attempts to converge from the guess `x1` while avoiding the previous converged solution close to `sol0`. This is very handy for branch switching. The method is based on a deflated Newton-Krylov solver.

# Arguments

Compared to [`newton`](@ref), the only different arguments are

  * `defOp::DeflationOperator` deflation operator
  * `linsolver` linear solver used to invert the Jacobian of the deflated functional.

      * custom solver `DeflatedProblemCustomLS()` which requires solving two linear systems `J⋅x = rhs`.
      * For other linear solvers `<: AbstractLinearSolver`, a matrix free method is used for the deflated functional.
      * if passed `Val(:autodiff)`, then `ForwardDiff.jl` is used to compute the jacobian Matrix of the deflated problem
      * if passed `Val(:fullIterative)`, then a full matrix free method is used for the deflated problem.
