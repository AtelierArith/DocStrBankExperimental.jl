```
pstimeresp(sys, u, t, x0 = zeros(sys.nx); state_history = false, solver, reltol, abstol) -> (y, tout, x)
```

Compute the time response of a periodic system `sys = (A(t),B(t),C(t),D(t))` to the input signals  described by `u` and `t`. The time vector `t` consists of regularly spaced time samples.  The input `u` can be specified as a matrix with as many columns as the number of inputs of `sys`,  in which case its `i`-th row specifies the input values at time `t[i]`.  For a discrete-time system, `u` should be sampled at the same sampling rate `Ts` as `sys` and `t` must have all time steps equal to `Ts` or can be set to an empty vector.  For continuous-time models, the input values are interpolated between samples using   zero-order hold based interpolation.  The vector `x0` specifies the initial state vector at time `t[1]` and is set to zero when omitted. 

The matrix `y` contains the resulting time history of the outputs of `sys` and  the vector `tout` contains the corresponding values of the time samples. The `i`-th row of `y` contains the output values at time `tout[i]`.   If the keyword parameter value `state_history = true` is used, then the matrix `x` contains  the resulting time history of the state vector and its `i`-th row `x[i,:]` contains  the state values at time `tout[i]`.  The column dimension of the matrix `x` is `n`, the dimension of the state vector.  For a discrete-time periodic system with time-varying state dimensions, `n` is the maximum value of the  dimensions of the state vector over one period. The components of `x[i,:]` have trailing zero values if the  corresponding state vector dimension is less than `n`.   By default, the state history is not saved and `x = nothing`.

For a continuous-time model an equivalent discretized model is determined to be used for simulation. The discretization is performed by determining the monodromy matrix as a product of  state transition matrices of the extended state-space matrix `[A(t) B(t); 0 0]`  by integrating numerically the corresponding homogeneous linear ODE.   The ODE solver to be employed can be  specified using the keyword argument `solver`, together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`),  absolute accuracy `abstol` (default: `abstol = 1.e-7`) and/or  the fixed step length `dt` (default: `dt = Ts/10`). Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "linear"` - use a special solver for linear ODEs (`MagnusGL6()`) with fixed time step `dt`;

`solver = "symplectic"` - use a symplectic Hamiltonian structure preserving solver (`IRKGL16()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

For large numbers of product terms, parallel computation of factors can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable. 
