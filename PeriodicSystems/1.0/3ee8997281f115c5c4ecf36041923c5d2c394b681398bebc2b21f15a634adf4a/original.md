```
pstimeresp(sys, u, t, x0 = zeros(sys.nx); state_history = false, solver, reltol, abstol) -> (y, tout, x)
```

Compute the time response of a continuous-time periodic system `sys = (A(t),B(t),C(t),D(t))` to the input signals  described by `u` and `t`. The time vector `t` consists of regularly spaced time samples.  The input `u` is specified as a vector of time dependent signals  with as many components as the number of inputs of `sys`.  The vector `x0` specifies the initial state vector at time `t[1]` and is set to zero when omitted. 

The matrix `y` contains the resulting time history of the outputs of `sys` and  the vector `tout` contains the corresponding values of the time samples. The `i`-th row of `y` contains the output values at time `tout[i]`.   If the keyword parameter value `state_history = true` is used, then the matrix `x` contains  the resulting time history of the state vector and its `i`-th row contains  the state values at time `tout[i]`. By default, the state history is not computed and `x = nothing`.

The ODE solver to be employed can be  specified using the keyword argument `solver` (see below), together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`),  absolute accuracy `abstol` (default: `abstol = 1.e-7`) and  the fixed step length `dt` (default: `dt = 0`), only used if `solver = "symplectic"`.  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "linear"` - use a special solver for linear ODEs (`MagnusGL6()`) with fixed time step `dt`;

`solver = "symplectic"` - use a symplectic Hamiltonian structure preserving solver (`IRKGL16()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 
