Iteratively Reweighted Least Square with Conjugate Gradient. This is the standard (expensive) IWLS but with more efficient solves to avoid full matrix computations.

## Parameters

  * `max_iter` (Int): number of max iterations (outer)
  * `max_inner` (Int): number of iterations for the CG solves
  * `tol` (Float64): tolerance for the relative change θ ie `norm(θ-θ_)/norm(θ)`
  * `damping` (Float64): how much to trust iterates (1=full trust)
  * `threshold` (Float64): threshold for the residuals
