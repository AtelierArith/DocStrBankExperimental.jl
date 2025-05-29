```
suggest_timestep(sys, integrator; tol)
```

Suggests a timestep for the numerical integration of spin dynamics according to a given error tolerance `tol`. The `integrator` should be [`Langevin`](@ref) or [`ImplicitMidpoint`](@ref). The suggested $dt$ will be inversely proportional to the magnitude of the effective field $|dE/d𝐒|$ arising from the current spin configuration in `sys`. The recommended timestep $dt$ scales like `√tol`, which assumes second-order accuracy of the integrator.

The system `sys` should be initialized to an equilibrium spin configuration for the target temperature. Alternatively, a reasonably timestep estimate can be obtained from any low-energy spin configuration. For this, one can use [`randomize_spins!`](@ref) and then [`minimize_energy!`](@ref).

Large `damping` magnitude or target temperature `kT` will tighten the timestep bound. If `damping` exceeds 1, it will rescale the suggested timestep by an approximate the factor $1/damping$. If `kT` is the largest energy scale, then the suggested timestep will scale like `1/(damping*kT)`. Quantification of numerical error for stochastic dynamics is subtle. The stochastic Heun integration scheme is weakly convergent of order-1, such that errors in the estimates of averaged observables may scale like `dt`. This implies that the `tol` argument may actually scale like the *square* of the true numerical error, and should be selected with this in mind.
