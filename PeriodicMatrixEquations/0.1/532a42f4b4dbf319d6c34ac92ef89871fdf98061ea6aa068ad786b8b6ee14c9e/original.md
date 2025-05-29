```
pgcplyap(A, C[, K = 1]; adj = false, solver, reltol, abstol) -> U
```

Compute upper triangular periodic generators `U(t)` of the solution `X(t) = U(t)U(t)'` of the  periodic Lyapunov differential equation

```
.
X(t) = A(t)X(t) + X(t)A(t)' + C(t)C(t)' , if adj = false,
```

or of the solution `X(t) = U(t)'U(t)` of the periodic Lyapunov differential equation

```
 .
-X(t) = A(t)'X(t) + X(t)A(t) + C(t)'C(t) , if adj = true.
```

The periodic matrices `A` and `C` must have the same type, commensurate periods and `A` must be stable. The resulting `U` is a collection of periodic generator matrices determined  as a periodic time-series matrix with `N` components, where `N = 1` if `A` and `C` are constant matrices and `N = K` otherwise.  The period of `U` is set to the least common commensurate period of `A` and `C` and the number of subperiods is adjusted accordingly. Any component matrix of `U` is a valid initial value to be used to generate the   solution over a full period by integrating the appropriate differential equation.  An extension of the multiple-shooting method of [1] is employed, first, to convert the continuous-time periodic Lyapunov  into a discrete-time periodic Lyapunov equation satisfied by  the generator solution in `K` time grid points and then to compute the solution by solving an appropriate discrete-time periodic Lyapunov  equation using the iterative method (Algorithm 5) of [2]. 

The ODE solver to be employed to convert the continuous-time problem into a discrete-time problem can be specified using the keyword argument `solver`,  together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`) and   absolute accuracy `abstol` (default: `abstol = 1.e-7`). Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

For large values of `K`, parallel computation of the matrices of the discrete-time problem can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  

*References*

[1] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation.      Proc. IEEE CDC/ECC, Seville, 2005. 

[2] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.      Int. J. Control, vol, 67, pp, 69-87, 1997.
