```
ModifiedVerlet <: Closure
```

Implements the modified Verlet Closure $b(r) = -\frac{\gamma^2(r)/2}{1+\alpha \gamma(r)}$. If $\gamma(r)<0$, the closure reads $-\gamma^2/2$. Example:

```julia
closure = ModifiedVerlet(0.2)
```

References:

Verlet, Loup. "Integral equations for classical fluids: I. The hard sphere case." Molecular Physics 41.1 (1980): 183-190.
