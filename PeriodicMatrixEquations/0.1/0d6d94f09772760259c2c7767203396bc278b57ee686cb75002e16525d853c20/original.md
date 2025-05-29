```
pgclyap2(A, C, E, [, K = 1]; solver, reltol, abstol) -> (X,Y)
```

Compute the solutions of the periodic differential Lyapunov equations

```
 .
 X(t) = A(t)*X(t) + X(t)*A'(t) + C(t)
```

and 

```
 .
-Y(t) = A(t)'*Y(t) + Y(t)*A(t) + E(t).
```

The periodic matrices `A`, `C` and `E` must have the same dimensions, the same type and  commensurate periods. Additionally `C` and `E` must be symmetric.   The allowed types are `PeriodicFunctionMatrix`, `PeriodicSymbolicMatrix` and `HarmonicArray`.

`K` specifies the number of grid points to be used for the discretization of the continuous-time problem (default: `K = 1`).  If `A`, `C` and `E` have the types `PeriodicFunctionMatrix`, `HarmonicArray`, `FourierFunctionMatrix` or `PeriodicSymbolicMatrix`,  then the resulting `X` and `Y` are collections of periodic generator matrices determined  as periodic time-series matrices with `N` components, where `N = 1` if `A`, `C` and `E` are constant matrices and `N = K` otherwise.      The period of `X` and `Y` is set to the least common commensurate period of `A`, `C` and `E` and the number of subperiods is adjusted accordingly. Any component matrix of `X` or `Y` is a valid initial value to be used to generate the   solution over a full period by integrating the appropriate differential equation.  The multiple-shooting method of [1] is employed, first, to convert the continuous-time periodic Lyapunov equations  into discrete-time periodic Lyapunov equations satisfied by  the generator solutions in the grid points and then to compute the solutions by solving appropriate discrete-time periodic Lyapunov  equations using the periodic Schur method of [2]. 

The ODE solver to be employed to convert the continuous-time problems into discrete-time problems can be specified using the keyword argument `solver`,  together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`) and   absolute accuracy `abstol` (default: `abstol = 1.e-7`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

Parallel computation of the matrices of the discrete-time problem can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  

*References*

[1] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation.      Proc. IEEE CDC/ECC, Seville, 2005. 

[2] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.      Int. J. Control, vol, 67, pp, 69-87, 1997.  
