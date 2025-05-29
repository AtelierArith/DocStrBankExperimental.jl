Sparse (semi-)nonnegative Tucker decomposition

Decomposes nonnegative tensor `tnsr` into optionally nonnegative `core` tensor and sparse nonnegative factor matrices `factors`.

  * `tnsr` nonnegative `N`-mode tensor to decompose
  * `core_dims` size of a core densor
  * `core_nonneg` if true, the output core tensor is nonnegative
  * `tol` the target error of decomposition relative to the Frobenius norm of `tnsr`
  * `max_iter` maximum number of iterations if error stays above `tol`
  * `max_time` max running time
  * `lambdas` `N+1` vector of non-negative sparsity regularizer coefficients for the factor matrices and the core tensor
  * `Lmin` lower bound for Lipschitz constant for the gradients of the residual error eqn{l(Z,U) = fnorm(tnsr - ttl(Z, U))`by`Z`and each`U`
  * `rw` controls the extrapolation weight
  * `bounds` `N+1` vector of the maximal absolute values allows for the elements of core tensor and factor matrices (effective only if the regularization is disabled)
  * `ini_decomp` initial decomposition, if equals to `:hosvd`, `hosvd()` is used to generate the starting decomposition, if `nothing`, a random decomposition is used
  * `verbose` more output algorithm progress

Returns:

  * `Tucker` decomposition object with additional properties:

```
* `:converged` method convergence indicator
* `:rel_residue` the Frobenius norm of the residual error `l(Z,U)` plus regularization penalty (if any)
* `:niter` number of iterations
* `:nredo` number of times `core` and `factor` were recalculated to avoid the increase in objective function
* `:iter_diag` convergence info for each iteration, see `SPNNTuckerState`
```

The function uses the alternating proximal gradient method to solve the following optimization problem:  deqn{min 0.5 |tnsr - Z times*1 U*1 ldots times*K U*K |*{F^2} +  sum*{n=1}^{K} lambda*n |U*n|*1 + lambda*{K+1} |Z|*1, ;text{where; Z geq 0, U*i geq 0.}  If `core_nonneg` is `FALSE`, core tensor `Z` is allowed to have negative  elements and eqn{z*{i,j}=max(0,z*{i,j}-lambda*{K+1}/L*{K+1}}) rule is replaced by eqn{z*{i,j}=sign(z*{i,j})max(0,|z*{i,j}|-lambda*{K+1}/L_{K+1})}.  The method stops if either the relative improvement of the error is below the tolerance `tol` for 3 consequitive iterations or  both the relative error improvement and relative error (wrt the `tnsr` norm) are below the tolerance.  Otherwise it stops if the maximal number of iterations or the time limit were reached.

The implementation is based on ntds_fapg() MATLAB code by Yangyang Xu and Wotao Yin.

See Y. Xu, "Alternating proximal gradient method for sparse nonnegative Tucker decomposition", Math. Prog. Comp., 7, 39-70, 2015. See http://www.caam.rice.edu/~optimization/bcu/`
