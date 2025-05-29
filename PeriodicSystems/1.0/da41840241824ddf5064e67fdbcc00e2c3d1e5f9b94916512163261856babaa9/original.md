```
psh2norm(psys; adj = false, smarg = 1, fast = false, offset = sqrt(ϵ)) -> nrm
```

Compute the H2-norm of a discrete-time periodic system `psys = (A(t),B(t),C(t),D(t))`.   For the computation of the norm, the formulas given in [1] are employed.  For `adj = false` the norm is computed as

```
 nrm = sqrt(sum(tr(C(t)P(t)C(t)'+D(t)*D(t)'))),
```

where `P(t)` is the controllability Gramian satisfying the periodic Lyapunov equation

```
 P(t+1) = A(t)P(t)A(t)' + B(t)B(t)',
```

while for `adj = true` the norm is computed as

```
nrm = sqrt(sum(tr(B(t)'Q(t+1)B(t)+D(t)'*D(t)))),
```

where `Q(t)` is the observability Gramian satisfying the periodic Lyapunov equation

```
Q(t) = A(t)'Q(t+1)A(t) + C(t)'C(t) .
```

The norm is set to infinity for an unstable system.

To assess the stability, the absolute values of the characteristic multipliers of `A(t)`  must be less than `smarg-β`, where `smarg` is the discrete-time stability margin (default: `smarg = 1`)  and  `β` is an offset specified via the keyword parameter `offset = β` to be used to numerically assess the stability of eigenvalues. The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

If `fast = false` (default) then the norm is evaluated using an approach based on the periodic Schur decomposition of `A(t)`,  while if `fast = true` the norm of the lifted standard system is evaluated.   This later option may occasionally lead to inaccurate results for large number of matrices. 

*References*

[1] S. Bittanti and P. Colaneri. Periodic Systems : Filtering and Control.     Springer-Verlag London, 2009. 
