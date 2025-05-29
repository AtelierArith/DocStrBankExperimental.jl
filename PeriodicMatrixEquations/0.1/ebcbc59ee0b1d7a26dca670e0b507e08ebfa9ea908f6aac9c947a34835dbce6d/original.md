```
pcric(A, R, Q; K = 10, N = 1, adj = false, solver, reltol, abstol, fast, intpol, dt) -> (X, EVALS)
```

Solve the periodic Riccati differential equation

```
.                                                 
X(t) = A(t)X(t) + X(t)A(t)' + Q(t) - X(t)R(t)X(t) ,  if adj = false,
```

or 

```
 .                                                
-X(t) = A(t)'X(t) + X(t)A(t) + Q(t) - X(t)R(t)X(t) , if adj = true
```

and compute the stable closed-loop characteristic multipliers in `EVALS` (see [`pgcric`](@ref) for details).

The periodic matrices `A`, `R` and `Q` must have the same type, the same dimensions and commensurate periods,  and additionally `R` and `Q` must be symmetric. The resulting symmetric periodic solution `X` has the type `PeriodicFunctionMatrix` and  `X(t)` can be used to evaluate the value of `X` at time `t`.  `X` has the period set to the least common commensurate period of `A`, `R` and `Q` and  the number of subperiods is adjusted accordingly.  *Note:* Presently the `PeriodicTimeSeriesMatrix` and `PeriodicSwitchingMatrix` types are not supported. 

If `fast = true` (default) the multiple-shooting method is used in conjunction with fast pencil reduction techniques, as proposed in [1], to determine the periodic solution in `t = 0` and a multiple point generator of the appropriate periodic differential Riccati equation is determined  (see [2] for details).  If `fast = false`, the multiple-shooting method is used in  conjunction with the periodic Schur decomposition to determine multiple point generators directly from the stable periodic invariant subspace of  an appropriate symplectic transition matrix (see also [2] for more details). 

For the determination of the multiple point periodic generators an implicit Runge-Kutta Gauss-Legendre 16th order method from the [IRKGaussLegendre.jl](https://github.com/SciML/IRKGaussLegendre.jl) package is employed to integrate the appropriate Hamiltonian system [2]. 

For the evaluation of solution via interpolation or ODE integration, the  following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected using the keyword argument `solver`: 

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

The accuracy of the computed solutions can be controlled via  the relative accuracy keyword `reltol` (default: `reltol = 1.e-4`) and  absolute accuracy keyword `abstol` (default: `abstol = 1.e-7`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

For large values of `K`, parallel computation can be used to determine  the matrices of the discrete-time problem or the multiple domain interpolation based  solutions. This requires to start Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  

*References*

[1] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation.      Proc. IEEE CDC/ECC, Seville, 2005. 

[2] A. Varga. On solving periodic Riccati equations.       Numerical Linear Algebra with Applications, 15:809-835, 2008.    
