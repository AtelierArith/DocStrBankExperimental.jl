```
modifying_integrator(series_integrator)
```

Compute the B-series of a "modifying integrator" equation of the time integration method with B-series `series_integrator`.

Given an ordinary differential equation (ODE) $u'(t) = f(u(t))$ and a Runge-Kutta method, the idea is to find a modified ODE $u'(t) = fₕ(u(t))$ such that the numerical solution with given time step size is the exact solution of the original ODE. This method returns the B-series of $h fₕ$.

!!! note "Normalization by elementary differentials"
    The coefficients of the B-series returned by this method need to be multiplied by a power of the time step divided by the `symmetry` of the rooted tree and multiplied by the corresponding elementary differential of the input vector field $f$. See also [`evaluate`](@ref).


# References

Section 3.2 of

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
