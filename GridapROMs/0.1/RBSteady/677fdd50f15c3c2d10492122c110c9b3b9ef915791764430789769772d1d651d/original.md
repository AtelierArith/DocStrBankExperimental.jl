```
struct RBSolver{A<:GridapType,B} <: GridapType
  fesolver::A
  state_reduction::Reduction
  residual_reduction::Reduction
  jacobian_reduction::B
end
```

Wrapper around a FE solver (e.g. `NonlinearSolver` or `ODESolver` in [`Gridap`](@ref)) with additional information on the reduced basis (RB) method employed to solve a given problem dependent on a set of parameters. A RB method is a projection-based reduced order model where

1. a suitable subspace of a FESpace is sought, of dimension n << Nₕ
2. a matrix-based discrete empirical interpolation method (MDEIM) is performed

to approximate the manifold of the parametric residuals and jacobians

3. the EIM approximations are compressed with (Petrov-)Galerkin projections

onto the subspace

4. for every desired choice of parameters, numerical integration is performed, and

the resulting n × n system of equations is cheaply solved

In particular:

  * tol: tolerance used in the projection-based truncated proper orthogonal decomposition (TPOD) or in the tensor train singular value decomposition (TT-SVD), where a basis spanning the reduced subspace is computed; the value of tol is responsible for selecting the dimension of the subspace, i.e. n = n(tol)
  * nparams_state: number of snapshots considered when running TPOD or TT-SVD
  * nparams_res: number of snapshots considered when running MDEIM for the residual
  * nparams_jac: number of snapshots considered when running MDEIM for the jacobian
  * nparams_test:  number of snapshots considered when computing the error the RB method commits with respect to the FE procedure
