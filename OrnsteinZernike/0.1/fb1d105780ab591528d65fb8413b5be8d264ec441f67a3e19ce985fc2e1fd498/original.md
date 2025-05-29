```
Verlet <: Closure
```

Implements the Verlet Closure $b(r) = -\frac{A\gamma^2(r)/2}{1+B \gamma(r)/2}$, where by default $A=1$ and $B=8/5$. These values are tuned by the virial coefficients of the 3d hard sphere liquid.

Example:

```julia
closure = Verlet()
closure = Verlet(A=3.0, B=4.0)
```

References:

Verlet, Loup. "Integral equations for classical fluids: I. The hard sphere case." Molecular Physics 41.1 (1980): 183-190.
