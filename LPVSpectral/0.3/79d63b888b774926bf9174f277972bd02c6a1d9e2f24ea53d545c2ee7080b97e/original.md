`ls_spectral_lpv(Y,X,V,w,Nv::Int; λ = 1e-8, coulomb = false, normalize=true)`

Perform LPV spectral estimation using the method presented in Bagge Carlson et al. "Linear Parameter-Varying Spectral Decomposition." See the paper For additional details.

`Y` output

`X` sample locations

`V` scheduling signal

`w` frequency vector

`Nv` number of basis functions

`λ` Regularization parameter

`coulomb` Assume discontinuity at `v=0` (useful for signals where, e.g., Coulomb friction might cause issues.)

`normalize` Use normalized basis functions (See paper for details).

The method will issue a warning If less than 90% of the variance in `Y` is described by the estimated model. If this is the case, try increasing either the number of frequencies or the number of basis functions per frequency. Alternatively, try lowering the regularization parameter `λ`.

See also `psd`, `ls_sparse_spectral_lpv` and `ls_windowpsd_lpv`
