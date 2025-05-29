Type for storing statistics returned by the majority of (block) Krylov solvers.

The fields are as follows:

  * `niter`: The total number of iterations completed by the solver;
  * `solved`: Indicates whether the solver successfully reached convergence (`true` if solved, `false` otherwise);
  * `inconsistent`: Flags whether the system was detected as inconsistent (i.e., when `b` is not in the range of `A`);
  * `indefinite`: Flags whether the system was detected as indefinite (i.e., when `A` is not positive definite);
  * `residuals`: A vector containing the residual norms at each iteration;
  * `Aresiduals`: A vector of `A'`-residual norms at each iteration;
  * `Acond`: An estimate of the condition number of matrix `A`.
  * `timer`: The elapsed time (in seconds) taken by the solver to complete all iterations;
  * `status`: A string indicating the outcome of the solve, providing additional details beyond `solved`.
