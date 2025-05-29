```
DuhHaymet <: Closure
```

Implements the Duh-Haymet closure $b(r) = \frac{-\gamma^*(r)^2}{2\left[1+\left(\frac{5\gamma^*(r)+11}{7\gamma^*(r)+9}\right)\gamma^*(r)\right]} $ for $\gamma^*(r) >0$, and $b(r)=-\gamma^*(r)^2/2$ otherwise. Here  $\gamma^* = \gamma - u_{LR}$ , in which $ u_{LR}$ is the long range tail of the potential, 

Example:

```julia
closure = DuhHaymet()
```

References:
