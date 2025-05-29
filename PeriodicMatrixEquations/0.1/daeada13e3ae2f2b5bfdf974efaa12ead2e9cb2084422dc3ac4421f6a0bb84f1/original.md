```
pgcric(A, R, Q[, K = 1]; adj = false, solver, reltol, abstol, fast, PSD_SLICOT) -> (X, EVALS)
```

Compute periodic generators for the periodic Riccati differential equation in the *filtering* form

```
.                                                  
X(t) = A(t)X(t) + X(t)A(t)' + Q(t) - X(t)R(t)X(t), if adj = false,
```

or in the *control* form

```
 .                                              
-X(t) = A(t)'X(t) + X(t)A(t) + Q(t) - X(t)R(t)X(t) , if adj = true,
```

where `A(t)`, `R(t)` and `Q(t)` are periodic matrices of commensurate periods,  with `A(t)` square, `R(t)` symmetric and positive definite, and `Q(t)` symmetric and positive semidefinite.  The resulting `X` is a collection of periodic generator matrices determined  as a periodic time-series matrix with `N` components, where `N = 1` if `A(t)`, `R(t)` and `Q(t)` are constant matrices and `N = K` otherwise.  `EVALS` contains the stable characteristic multipliers of the monodromy matrix of  the corresponding Hamiltonian matrix (also called closed-loop characteristic multipliers). The period of `X` is set to the least common commensurate period of `A(t)`, `R(t)` and `Q(t)` and the number of subperiods is adjusted accordingly.  Any component matrix of `X` is a valid initial value to be used to generate the   solution over a full period by integrating the appropriate differential equation. 

If `fast = true` (default) the multiple-shooting method is used in conjunction with fast pencil reduction techniques, as proposed in [1], to determine the periodic solution in `t = 0` and a multiple point generator of the appropriate periodic differential Riccati equation is determined  (see [2] for details).  If `fast = false`, the multiple-shooting method is used in  conjunction with the periodic Schur decomposition to determine multiple point generators directly from the stable periodic invariant subspace of  an appropriate symplectic transition matrix (see also [2] for more details). 

The recommended solver to integrate the appropriate Hamiltonian system [2] is the implicit Runge-Kutta Gauss-Legendre 16th order method from the [IRKGaussLegendre.jl](https://github.com/SciML/IRKGaussLegendre.jl) package, which can be selected with `solver = "symplectic"` (default).

Other ODE solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be also selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "linear"` - use a special solver for linear ODEs (`MagnusGL6()`) with fixed time step `dt`;

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

The accuracy of the computed solutions can be controlled via  the relative accuracy keyword `reltol` (default: `reltol = 1.e-4`) and  absolute accuracy keyword `abstol` (default: `abstol = 1.e-7`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

For large values of `K`, parallel computation of the matrices of the discrete-time problem can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  

*References*

[1] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation.      Proc. IEEE CDC/ECC, Seville, 2005. 

[2] A. Varga. On solving periodic Riccati equations.       Numerical Linear Algebra with Applications, 15:809-835, 2008.    
