```
pshanorm(psys; smarg = 1, lifting = false, offset = sqrt(ϵ)) -> nrm
```

Compute the Hankel-norm of a stable discrete-time periodic system `psys = (A(t),B(t),C(t),D(t))`.   For the computation of the norm, the formulas given in [1] are employed.  The Hankel norm is computed as

```
 nrm = maximum(sqrt(Λ(P(t)Q(t))),
```

where `P(t)` is the controllability Gramian satisfying the periodic Lyapunov equation

```
 P(t+1) = A(t)P(t)A(t)' + B(t)B(t)',
```

and `Q(t)` is the observability Gramian satisfying the periodic Lyapunov equation

```
Q(t) = A(t)'Q(t+1)A(t) + C(t)'C(t) .
```

To assess the stability, the absolute values of the characteristic multipliers of `A(t)`  must be less than `smarg-β`, where `smarg` is the discrete-time stability margin (default: `smarg = 1`)  and  `β` is an offset specified via the keyword parameter `offset = β` to be used to numerically assess the stability of eigenvalues. The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

If `lifting = false` (default), then the norm is evaluated using an approach based on the periodic Schur decomposition of `A(t)`,  while if `lifting = true` the norm of the lifted cyclic system is evaluated.   This later option may lead to excessive computational times for large matrices or large periods. 

*References*

[1] S. Bittanti and P. Colaneri. Periodic Systems : Filtering and Control.     Springer-Verlag London, 2009. 
