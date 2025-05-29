```
psh2norm(psys, K; adj = false, smarg = 1, fast = false, offset = sqrt(ϵ), solver = "auto", reltol = 1.e-4, abstol = 1.e-7, quad = false) -> nrm
```

Compute the H2-norm of a continuous-time periodic system `psys = (A(t),B(t),C(t),D(t))`.   For the computation of the norm, the formulas given in [1] are employed,  in conjunction with the multiple-shooting approach of [2] using `K` discretization points.   For a periodic system of period  `T`, for `adj = false` the norm is computed as

```
 nrm = sqrt(Integral(tr(C(t)P(t)C(t)')))dt/T),
```

where `P(t)` is the controllability Gramian satisfying the periodic differential Lyapunov equation

```
 .
 P(t) = A(t)P(t)A(t)' + B(t)B(t)',
```

while for `adj = true` the norm is computed as

```
nrm = sqrt(Integral(tr(B(t)'Q(t)B(t)))dt/T),
```

where Q(t) is the observability Gramian satisfying the periodic differential Lyapunov equation

```
 .
-Q(t) = A(t)'Q(t)A(t) + C(t)'C(t) .
```

If `quad = true`, a simple quadrature formula based on the sum of time values is employed (see [2]). This option ensures a faster evaluation, but is potentially less accurate then the exact evaluation employed if `quad = false` (default). 

The norm is set to infinity for an unstable system or for a non-zero `D(t)`.

To assess the stability, the absolute values of the characteristic multipliers of `A(t)`  must be less than `smarg-β`, where `smarg` is the discrete-time stability margin (default: `smarg = 1`)  and  `β` is an offset specified via the keyword parameter `offset = β` to be used to numerically assess the stability of eigenvalues. The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision.  If `fast = false` (default) then the stability is checked using an approach based on the periodic Schur decomposition of `A(t)`,  while if `fast = true` the stability is checked using a lifting-based approach.  

The ODE solver to be employed to convert the continuous-time problem into a discrete-time problem can be specified using the keyword argument `solver`,  together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`) and   absolute accuracy `abstol` (default: `abstol = 1.e-7`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

*References*

[1] P. Colaneri. Continuous-time periodic systems in H2 and H∞: Part I: Theoretical Aspects.     Kybernetika, 36:211-242, 2000. 

[2] A. Varga, On solving periodic differential matrix equations with applications to periodic system norms computation.     Proc. CDC/ECC, Seville, p.6545-6550, 2005.  
