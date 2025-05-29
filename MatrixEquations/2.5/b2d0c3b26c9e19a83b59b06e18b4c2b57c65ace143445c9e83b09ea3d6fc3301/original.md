```
plyapdi(A, E, B; cyclic, abstol, reltol, maxiter, nshifts, shifts, loginf) -> (U, info)
plyapdi(A, B; cyclic, abstol, reltol, maxiter, nshifts, shifts, loginf) -> (U, info)
```

Compute a low-rank factor `U` of the solution `X = UU'` of the generalized discrete Lyapunov equation

```
  AXA' - EXE' + BB' = 0,
```

where `A` and `E` are square real matrices and `B` is a real matrix with the same number of rows as `A`. The pencil `A - λE` must have only eigenvalues with moduli less than one. `E = I` is assumed in the second call. 

The named tuple `info` contains information related to the execution of the LR-ADI algorithm as follows: `info.niter` contains the number of performed iterations;  `info.res_fact` contains the norm of the residual factor;  `info.res` contains, if `loginf = true`, the vector of normalized residual norms (normalized with respect to the norm of the initial approximation); `info.rc` contains, if `loginf = true`, the vector of norms of relative changes in building the solution; `info.used_shift` contains the vector of used shifts.

The keyword argument `abstol` (default: `abstol = 1e-12`) is the tolerance used for convergence test on the normalized residuals, while the keyword argument `reltol` (default: `reltol = 0`) is the tolerance for the relative changes of the solution.  The keyword argument `maxiter` can be used to set the maximum number of iterations (default: `maxiter = 100`). The keyword argument `nshifts` specifies the desired number of shifts to be used in an iteration cycle (default: `nshifts = 6`).  The keyword argument `shifts` can be used to provide a pre-calculated set of complex conjugated shifts to be used to start the iterations (default: `shifts = missing`). With the keyword argument `loginf = true`, the normalized residual values and the norms of increments of the solution can be saved as outputs in the resulting info structure (default: `loginf = false`). 

The low-rank ADI (LR-ADI) method with enhancements proposed in [1] is adapted to the discrete case,  inspired by the MATLAB codes of the free software described in [2]. If `cyclic = true`, the cyclic low-rank method of [3] is adapted, with the pre-calculated shifts provided in the keyword argument `shifts`. 

*References*

[1] P. Kürschner. Efficient Low-Rank Solution of Large-Scale Matrix Equations.      Dissertation, Otto-von-Guericke-Universität, Magdeburg, Germany, 2016. Shaker Verlag,

[2] P. Benner, M. Köhler, and J. Saak. “Matrix Equations, Sparse Solvers: M-M.E.S.S.-2.0.1—     Philosophy, Features, and Application for (Parametric) Model Order Reduction.”      In Model Reduction of Complex Dynamical Systems, Eds. P. Benner et.al., 171:369–92, Springer, 2021.

[3] T. Penzl, A cyclic low-rank Smith method for large sparse Lyapunov equations,      SIAM J. Sci. Comput. 21 (4) (1999) 1401–1418.
