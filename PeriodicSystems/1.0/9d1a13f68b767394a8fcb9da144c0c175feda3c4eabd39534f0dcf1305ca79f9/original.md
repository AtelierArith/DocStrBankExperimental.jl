```
pshanorm(psys, K; smarg = 1, offset = sqrt(ϵ), solver = "auto", reltol = 1.e-4, abstol = 1.e-7) -> nrm
```

Compute the Hankel-norm of a stable continuous-time periodic system `psys = (A(t),B(t),C(t),D(t))`.   For the computation of the norm, the approach suggested in [1] is employed,  in conjunction with the multiple-shooting approach using `K` discretization points.   For a periodic system of period  `T`, the Hankel-norm is defined as

```
 nrm = sqrt(max(Λ(P(t)Q(t)))), for t ∈ [0,T]
```

where `P(t)` is the controllability Gramian satisfying the periodic differential Lyapunov equation

```
 .
 P(t) = A(t)P(t)A(t)' + B(t)B(t)',
```

and `Q(t)` is the observability Gramian satisfying the periodic differential Lyapunov equation

```
 .
-Q(t) = A(t)'Q(t)A(t) + C(t)'C(t) .
```

The norm is evaluated from the `K` time values of `P(t)` and `Q(t)` in the interval `[0,T]` and  the precision is (usually) better for larger values of `K`.

To assess the stability, the absolute values of the characteristic multipliers of `A(t)`  must be less than `smarg-β`, where `smarg` is the discrete-time stability margin (default: `smarg = 1`)  and  `β` is an offset specified via the keyword parameter `offset = β` to be used to numerically assess the stability of eigenvalues. The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The ODE solver to be employed to convert the continuous-time problem into a discrete-time problem can be specified using the keyword argument `solver`,  together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`) and   absolute accuracy `abstol` (default: `abstol = 1.e-7`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

*References*

[1] A. Varga, On solving periodic differential matrix equations with applications to periodic system norms computation.     Proc. CDC/ECC, Seville, p.6545-6550, 2005.  
