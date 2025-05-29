`CHOLMODFactorization(; shift = 0.0, perm = nothing)`

A wrapper of CHOLMOD's polyalgorithm, mixing Cholesky factorization and ldlt. Tries cholesky for performance and retries ldlt if conditioning causes Cholesky to fail.

Only supports sparse matrices.

## Keyword Arguments

  * shift: the shift argument in CHOLMOD.
  * perm: the perm argument in CHOLMOD
