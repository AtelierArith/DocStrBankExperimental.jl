```
 psc2d([PMT,] psysc, Ts; solver, reltol, abstol, dt) -> psys::PeriodicStateSpace{PMT}
```

Compute for the continuous-time periodic system `psysc = (A(t),B(t),C(t),D(t))` of period `T` and  for a sampling time `Ts`, the corresponding discretized periodic system `psys = (Ad,Bd,Cd,Dd)` using a zero-order hold based discretization method.  The resulting discretized system `psys` has the matrices of type `PeriodicArray` by default, or of type `PMT`, where `PMT` is one of the types `PeriodicMatrix`, `PeriodicArray`, `SwitchingPeriodicMatrix` or `SwitchingPeriodicArray`.    

The discretization is performed by determining the monodromy matrix as a product of  `K = T/Ts` state transition matrices of the extended state-space matrix `[A(t) B(t); 0 0]`  by integrating numerically the corresponding homogeneous linear ODE.   The ODE solver to be employed can be  specified using the keyword argument `solver`, together with the required relative accuracy `reltol` (default: `reltol = 1.e-3`),  absolute accuracy `abstol` (default: `abstol = 1.e-7`) and/or  the fixed step length `dt` (default: `dt = Ts/10`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "linear"` - use a special solver for linear ODEs (`MagnusGL6()`) with fixed time step `dt`;

`solver = "symplectic"` - use a symplectic Hamiltonian structure preserving solver (`IRKGL16()`);

`solver = ""` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

For large values of `K`, parallel computation of factors can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  
