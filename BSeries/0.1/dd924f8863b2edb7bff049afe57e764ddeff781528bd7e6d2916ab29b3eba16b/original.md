```
energy_preserving_order(rk::RungeKuttaMethod, max_order)
```

This function checks up to which order a Runge-Kutta method `rk` is energy-preserving for Hamiltonian problems. It requires a `max_order` so that it does not run forever if the order up to which the method is energy-preserving is too big or infinite.

See also [`is_energy_preserving`](@ref).
