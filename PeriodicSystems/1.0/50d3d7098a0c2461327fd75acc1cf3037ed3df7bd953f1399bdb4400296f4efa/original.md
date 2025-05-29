```
pslinfnorm(psys, K = 100; hinfnorm = false, rtolinf = 0.001, offset = sqrt(ϵ), reltol, abstol, dt) -> (linfnorm, fpeak)
pshinfnorm(psys, K = 100; rtolinf = 0.001, offset = sqrt(ϵ), reltol, abstol, dt) -> (linfnorm, fpeak)
```

Compute for a continuous-time periodic system `psys = (A(t),B(t),C(t),D(t)` the `L∞` norm `linfnorm` with `pslinfnorm` or the  `H∞` norm `hinfnorm` with `pshinfnorm` as defined in [1].  If `hinfnorm = true`, the `H∞` norm is computed with `pslinfnorm`. The corresponding peak frequency `fpeak`, where the peak gain is achieved, is usually not determined, excepting in some limiting cases.    The `L∞` norm is infinite if `psys` has poles on the imaginary axis. 

To check the lack of poles on the imaginary axis, the characteristic exponents of `A(t)`  must not have real parts in the interval `[-β,β]`, where `β` is the stability domain boundary offset.   The offset  `β` to be used can be specified via the keyword parameter `offset = β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

A bisection based algorith, as described in [2], is employed to approximate the `L∞` norm, and the keyword argument `rtolinf` specifies the relative accuracy for the computed infinity norm.  The  default value used for `rtolinf` is `0.001`.

If `hinfnorm = true`, the `H∞` norm is computed.  In this case, the stability of the system is additionally checked and  the `H∞` norm is infinite for an unstable system. To check the stability, the characteristic exponents of `A(t)` must have real parts less than `-β`.

The ODE solver to be employed to compute the characteristic multipliers of the system Hamiltonian can be specified using the keyword argument `solver` (default: `solver = "symplectic"`)  together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`),   absolute accuracy `abstol` (default: `abstol = 1.e-7`) and  stepsize `dt` (default: `dt = 0`). The value stepsize is relevant only if `solver = "symplectic", in which case an adaptive stepsize strategy is used if`dt = 0`and a fixed stepsize is used if`dt > 0`. Depending on the desired relative accuracy`reltol`, lower order solvers are employed for`reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If`reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "linear"` - use a special solver for linear ODEs (`MagnusGL6()`) with fixed time step `dt`;

`solver = "symplectic"` - use a symplectic Hamiltonian structure preserving solver (`IRKGL16()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

*References:*    

[1] P. Colaneri. Continuous-time periodic systems in H2 and H∞: Part I: Theoretical Aspects.     Kybernetika, 36:211-242, 2000. 

[2] A. Varga, On solving periodic differential matrix equations with applications to periodic system norms computation.     Proc. CDC/ECC, Seville, p.6545-6550, 2005.  
