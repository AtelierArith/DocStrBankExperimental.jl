```
 tvstm(A, tf, t0; solver, reltol, abstol, dt) -> Φ
```

Compute the state transition matrix for a linear ODE with periodic time-varying coefficients.  For the given square periodic continuous-time matrix `A(t)`, initial time `t0` and  final time `tf`, the state transition matrix `Φ(tf,t0)` is computed by integrating numerically the homogeneous linear ODE 

```
  dΦ(t,t0)/dt = A(t)Φ(t,t0),  Φ(t0,t0) = I
```

on the time interval `[t0,tf]`.   `A` may be given as a [`PeriodicFunctionMatrix`](@ref), a [`HarmonicArray`](@ref), a [`PeriodicSymbolicMatrix`](@ref) or a  [`FourierFunctionMatrix`](@ref). 

The ODE solver to be employed can be  specified using the keyword argument `solver` (see below), together with the required relative accuracy `reltol` (default: `reltol = 1.e-3`),  absolute accuracy `abstol` (default: `abstol = 1.e-7`) and/or  the fixed step length `dt` (default: `dt = tf-t0`).  Depending on the desired relative accuracy `reltol`,  lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "linear"` - use a special solver for linear ODEs (`MagnusGL6()`) with fixed time step `dt`;

`solver = "symplectic"` - use a symplectic Hamiltonian structure preserving solver (`IRKGL16()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 
