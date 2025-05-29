```
Lee <: Closure
```

Implements the Lee closure $b(r) = -\frac{\zeta\gamma^*(r)^2}{2} \left( 1- \frac{\phi \alpha \gamma^*(r)}{1 + \alpha\gamma^*(r)} \right) $. Here  $\gamma^* = \gamma + ρ f(r)/2$ , in which $ f(r)$ is the Mayer-f function and $\rho$ the density. Additionally, $\zeta$,$\phi$, and, $\alpha$ are free parameters that  can be determined with thermodynamic consistency or zero-separation theorems.

Example:

```julia
closure = Lee(1.073, 1.816, 1.0, 0.4) # ζ, ϕ, α, ρ
```

References:

Lee, Lloyd L. "An accurate integral equation theory for hard spheres: Role of the zero‐separation theorems in the closure relation." The Journal of chemical physics 103.21 (1995): 9388-9396.
