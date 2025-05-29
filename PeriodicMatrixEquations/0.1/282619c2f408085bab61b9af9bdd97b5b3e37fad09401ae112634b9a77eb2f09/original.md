```
pgclyap(A, C[, K = 1]; adj = false, solver, reltol, abstol) -> X
```

Compute periodic generators for the periodic Lyapunov differential equation

```
.
X(t) = A(t)X(t) + X(t)A(t)' + C(t) , if adj = false,
```

or 

```
 .
-X(t) = A(t)'X(t) + X(t)A(t) + C(t) , if adj = true.
```

The periodic matrices `A` and `C` must have the same type, the same dimensions and commensurate periods,  and additionally `C` must be symmetric.  `K` specifies the number of grid points to be used for the discretization of the continuous-time problem (default: `K = 1`).  If  `A` and `C` are of types `PeriodicTimeSeriesMatrix` or `PeriodicSwitchingMatrix`, then `K` specifies the number of grid points  used between two consecutive switching time values (default: `K = 1`).  

If `A` and `C` have the types `PeriodicFunctionMatrix`, `HarmonicArray`, `FourierFunctionMatrix` or `PeriodicTimeSeriesMatrix`,  then the resulting `X` is a collection of periodic generator matrices determined  as a *periodic time-series matrix* with `N` components, where `N = 1` if `A` and `C` are constant matrices and `N = K` otherwise.  If `A` and `C` have the type `PeriodicSwitchingMatrix`, then `X` is a collection of periodic generator matrices  determined as a *periodic switching matrix*, whose switching times are the unique switching times contained in the union of the switching times of `A` and `C`.  If `K > 1`, a refined grid of `K` equidistant values is used for each two consecutive  switching times in the union.      

The period of `X` is set to the least common commensurate period of `A` and `C` and the number of subperiods is adjusted accordingly. Any component matrix of `X` is a valid initial value to be used to generate the   solution over a full period by integrating the appropriate differential equation.  The multiple-shooting method of [1] is employed, first, to convert the continuous-time periodic Lyapunov differential equation  into a discrete-time periodic Lyapunov equation satisfied by  the generator solution in the grid points and then to compute the solution by solving an appropriate discrete-time periodic Lyapunov  equation using the periodic Schur method of [2]. 

The ODE solver to be employed to convert the continuous-time problem into a discrete-time problem can be specified using the keyword argument `solver`,  together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`) and   absolute accuracy `abstol` (default: `abstol = 1.e-7`). Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

Parallel computation of the matrices of the discrete-time problem can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  

*References*

[1] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation.      Proc. IEEE CDC/ECC, Seville, 2005. 

[2] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.      Int. J. Control, vol, 67, pp, 69-87, 1997.
