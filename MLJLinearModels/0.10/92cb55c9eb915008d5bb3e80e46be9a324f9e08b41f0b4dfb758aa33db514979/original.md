Proximal Gradient solver for non-smooth objective functions.

## Parameters

  * `accel` (Bool): whether to use Nesterov-style acceleration
  * `max_iter` (Int): number of overall iterations
  * `tol` (Float64): tolerance for the relative change θ ie `norm(θ-θ_)/norm(θ)`
  * `max_inner`: number of inner steps when searching for a stepsize in the              backtracking step
  * `beta`: rate of shrinkage in the backtracking step (between 0 and 1)
