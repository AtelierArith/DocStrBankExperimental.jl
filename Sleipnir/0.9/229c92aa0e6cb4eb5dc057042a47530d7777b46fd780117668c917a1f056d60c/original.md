A structure representing physical parameters used in simulations.

```
PhysicalParameters{F <: AbstractFloat}
```

# Fields

  * `ρ::F`: Density of ice.
  * `g::F`: Gravitational acceleration.
  * `ϵ::F`: A small parameter, often used for perturbations.
  * `η₀::F`: Initial viscosity.
  * `maxA::F`: Maximum A.
  * `minA::F`: Minimum A.
  * `maxTlaw::F`: Maximum temperature according to some law.
  * `minTlaw::F`: Minimum temperature according to some law.
  * `noise_A_magnitude::F`: Magnitude of noise in A.
