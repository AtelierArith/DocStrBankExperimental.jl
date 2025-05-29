```
pgclyap2(A, C::AbstractMatrix, E, [, K = 1]; solver, reltol, abstol) -> (X,Y)
```

Compute the solution of the discrete-time periodic Lyapunov equation

```
X(i+1) = Φ(i)*X(i)*Φ'(i) + W(i), i = 1, ..., K, X(K+1) := X(1)
```

and a periodic generator for the periodic Lyapunov differential equations

```
 .
-Y(t) = A(t)'Y(t) + Y(t)A(t) + E(t).
```

The periodic matrices `A` and `E` and the constant matrix `C` must have the same dimensions, and `A` and `E`  must have the same type and commensurate periods. Additionally `C` and `E` must be symmetric.   `Φ(i)` denotes the transition matrix on the time interval `[Δ*(i-1), Δ*i]` corresponding to `A`,  where `Δ = T/K` with `T` the common period of `A` and `E`. `W(i) = 0` for `i = 1, ..., K-1` and `W(K) = C`.   If `A` and `E` have the types `PeriodicFunctionMatrix`, `HarmonicArray`, `FourierFunctionMatrix` or `PeriodicSymbolicMatrix`,  then the resulting `Y` is a collection of periodic generator matrices determined  as a periodic time-series matrix with `N` components, where `N = 1` if `A` and `E` are constant matrices and `N = K` otherwise.      The period `T` of `Y` is set to the least common commensurate period of `A` and `E` and the number of subperiods is adjusted accordingly. Any component matrix of `Y` is a valid initial value to be used to generate the   solution over a full period by integrating the appropriate differential equation.  The multiple-shooting method of [1] is employed, first, to convert the continuous-time periodic Lyapunov into a discrete-time periodic Lyapunov equation satisfied by  the generator solution in the grid points and then to compute the solution by solving an appropriate discrete-time periodic Lyapunov  equation using the periodic Schur method of [2]. 

The ODE solver to be employed to convert the continuous-time problems into discrete-time problems can be specified using the keyword argument `solver`,  together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`) and   absolute accuracy `abstol` (default: `abstol = 1.e-7`). Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

Parallel computation of the matrices of the discrete-time problem can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  

*References*

[1] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation.      Proc. IEEE CDC/ECC, Seville, 2005. 

[2] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.      Int. J. Control, vol, 67, pp, 69-87, 1997.  
