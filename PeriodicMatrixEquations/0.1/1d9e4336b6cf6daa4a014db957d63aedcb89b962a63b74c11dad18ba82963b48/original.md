```
pclyap(A, C; K = 10, N = 1, adj = false, solver, reltol, abstol, intpol) -> X
```

Solve the periodic Lyapunov differential equation

```
.
X(t) = A(t)X(t) + X(t)A(t)' + C(t) , if adj = false,
```

or 

```
 .
-X(t) = A(t)'X(t) + X(t)A(t) + C(t) , if adj = true.
```

The periodic matrices `A` and `C` must have the same type, the same dimensions and commensurate periods.  Additionally `C` must be symmetric.  The resulting symmetric periodic solution `X` has the type `PeriodicFunctionMatrix` and  `X(t)` can be used to evaluate the value of `X` at time `t`.  `X` has the period set to the least common commensurate period of `A` and `C` and the number of subperiods is adjusted accordingly. 

The multiple-shooting method of [1] is employed to convert the (continuous-time) periodic differential Lyapunov equation  into a discrete-time periodic Lyapunov equation satisfied by a multiple point periodic generator of the solution.  The keyword argument `K` specifies the number of grid points to be used for the discretization of the continuous-time problem (default: `K = 10`).  If  `A` and `C` are of types `PeriodicTimeSeriesMatrix` or `PeriodicSwitchingMatrix`, then `K` specifies the number of grid points  used between two consecutive switching time values (default: `K = 1`).   The multiple point periodic generator is computed  by solving the appropriate discrete-time periodic Lyapunov  equation using the periodic Schur method of [2].  The obtained periodic generator is finally converted into a periodic function matrix which determines for a given `t`  the function value `X(t)` by interpolating the solution of the appropriate differential equations if `intpol = true` (default)   or by integrating the appropriate ODE from the nearest grid point value if `intpol = false`. For the interplation-based evaluation the integer keyword argument `N` can be used to split the integration domain (i.e., one period)  into `N` subdomains to perform the interpolations separately in each domain. The default value of `N` is `N = 1`.  

The ODE solver to be employed to convert the continuous-time problem into a discrete-time problem can be specified using the keyword argument `solver`, together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`) and  absolute accuracy `abstol` (default: `abstol = 1.e-7`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

Parallel computation of the matrices of the discrete-time problem can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  

*References*

[1] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation.      Proc. IEEE CDC/ECC, Seville, 2005. 

[2] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.      Int. J. Control, vol, 67, pp, 69-87, 1997.
