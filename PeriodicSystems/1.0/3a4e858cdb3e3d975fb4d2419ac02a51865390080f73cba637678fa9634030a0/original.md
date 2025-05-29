```
psstepresp(sys[, tfinal]; ustep = ones(psys.nu), x0 = zeros(psys.nx), timesteps = 100, 
         state_history = false, abstol, reltol) -> (y, tout, x)
```

Compute the time response of a periodic system `sys = (A(t),B(t),C(t),D(t))` to step input signals.  The final time `tfinal`, if not specified, is set equal to the period of the periodic system `sys`. For a discrete-time system, the final time `tfinal` must be commensurate with the system sampling time `Ts` (otherwise it is adjusted to the nearest smaller commensurate value).  The keyword argument `ustep` is a vector with as many components  as the inputs of `sys` and specifies the desired amplitudes of step inputs (default: all components are set to 1).    The keyword argument `x0` is a vector, which specifies the initial state vector at time `0`,  and is set to zero when omitted.  The keyword argument `timesteps` specifies the number of desired simulation time steps  (default: `timesteps = 100`). 

If `ns` is the total number of simulation values, `n` the number of state components,  `p` the number of system outputs and `m` the number of system inputs, then the resulting `ns×p×m` array `y` contains the resulting time histories of the outputs of `sys`, such  that `y[:,:,j]` is the time response for the `j`-th input set to `ustep[j]` and the rest of inputs set to zero.   The vector `tout` contains the corresponding values of the time samples. The `i`-th row `y[i,:,j]` contains the output values at time `tout[i]` of the `j`-th step response.   If the keyword parameter value `state_history = true` is used, then the resulting `ns×n×m` array`x` contains  the resulting time histories of the state vector and  the `i`-th row `x[i,:,j]` contains the state values at time `tout[i]` of the `j`-th step response.   For a discrete-time periodic system with time-varying state dimensions, `n` is the maximum value of the  dimensions of the state vector over one period. The components of `x[i,:,j]` have trailing zero values if the  corresponding state vector dimension is less than `n`.   By default, the state history is not saved and `x = nothing`.

The total number of simulation values `ns` is set as follows: for a continuous-time system `ns = timesteps+1`  and for a discrete-time system `ns = min(timesteps,tfinal/Ts)+1`. 

For a continuous-time model an equivalent discretized model is determined to be used for simulation, provided the time step `Δ = tfinal/timesteps` is commensurate with the system period `T` and `tfinal >= T`.  The discretization is performed by determining the monodromy matrix as a product of  state transition matrices of the extended state-space matrix `[A(t) B(t); 0 0]`  by integrating numerically the corresponding homogeneous linear ODE.   If the time step `Δ` is not commensurate with the period `T` or `tfinal < T`, then numerical integrations of the underlying ODE systems are performed.  The ODE solver to be employed can be  specified using the keyword argument `solver`, together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`),  absolute accuracy `abstol` (default: `abstol = 1.e-7`) and/or  the fixed step length `dt` (default: `dt = Ts/10`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "linear"` - use a special solver for linear ODEs (`MagnusGL6()`) with fixed time step `dt`;

`solver = "symplectic"` - use a symplectic Hamiltonian structure preserving solver (`IRKGL16()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

For large numbers of product terms, parallel computation of factors can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable. 
