Analytical solver (Cholesky). If the `iterative` parameter is set to `true` then a CG solver is used. The CG solver is matrix-free and should be preferred in "large scale" cases (when the hat matrix `X'X` is "big").

## Parameters

  * `iterative` (Bool): whether to use CG (iterative) or not
  * `max_inner` (Int): in the iterative mode, how many inner iterations to do.
