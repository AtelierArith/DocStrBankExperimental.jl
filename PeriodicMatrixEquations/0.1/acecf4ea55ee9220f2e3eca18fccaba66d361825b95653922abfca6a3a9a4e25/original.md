```
prcric(A, B, R, Q; K = 10, N = 1, solver, intpol, reltol, abstol, fast) -> (X, EVALS, F)
```

Compute the symmetric stabilizing solution `X(t)` of the periodic control related Riccati differential equation

```
 .                                                -1 
-X(t) = A(t)'X(t) + X(t)A(t) + Q(t) - X(t)B(t)R(t)  B(t)'X(t) ,
```

the periodic stabilizing state-feedback gain 

```
           -1
F(t) = R(t)  B(t)'X(t)
```

and the corresponding stable characteristic multipliers `EVALS` of `A(t)-B(t)F(t)`. 

The periodic matrices `A`, `B`, `R` and `Q` must have the same type and commensurate periods,  and additionally `R` must be symmetric positive definite and `Q` must be symmetric positive semidefinite.  The resulting symmetric periodic solution `X` has the period  set to the least common commensurate period of `A`, `B`, `R` and `Q` and the number of subperiods is adjusted accordingly. 

If `fast = true` (default) the multiple-shooting method is used in conjunction with fast pencil reduction techniques, as proposed in [1], to determine the periodic solution in `t = 0` and a multiple point generator of the appropriate periodic differential Riccati equation is determined  (see [2] for details).  If `fast = false`, the multiple-shooting method is used in  conjunction with the periodic Schur decomposition to determine multiple point generators directly from the stable periodic invariant subspace of  an appropriate symplectic transition matrix (see also [2] for more details). 

The keyword argument `K` specifies the number of grid points to be used for the resulting multiple point periodic generator (default: `K = 10`).  The obtained periodic generator is finally converted into a periodic function matrix which determines for a given `t`  the function value `X(t)` by interpolating the solution of the appropriate differential equations if `intpol = true` (default)   or by integrating the appropriate ODE from the nearest grid point value if `intpol = false`. For the interplation-based evaluation the integer keyword argument `N` can be used to split the integration domain (i.e., one period)  into `N` subdomains to perform the interpolations separately in each domain. The default value of `N` is `N = 1`.  

For the determination of the multiple point periodic generators an implicit Runge-Kutta Gauss-Legendre 16th order method from the [IRKGaussLegendre.jl](https://github.com/SciML/IRKGaussLegendre.jl) package is employed to integrate the appropriate Hamiltonian system [2]. 

For the evaluation of solution via interpolation or ODE integration, the  following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected using the keyword argument `solver`: 

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

The accuracy of the computed solutions can be controlled via  the relative accuracy keyword `reltol` (default: `reltol = 1.e-4`) and  absolute accuracy keyword `abstol` (default: `abstol = 1.e-7`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

For large values of `K`, parallel computation of the matrices of the discrete-time problem can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  

*References*

[1] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation.      Proc. IEEE CDC/ECC, Seville, 2005. 

[2] A. Varga. On solving periodic Riccati equations.       Numerical Linear Algebra with Applications, 15:809-835, 2008.    
