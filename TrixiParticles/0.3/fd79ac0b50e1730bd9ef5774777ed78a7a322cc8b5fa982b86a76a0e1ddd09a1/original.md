```
ArtificialViscosityMonaghan(; alpha, beta=0.0, epsilon=0.01)
```

Artificial viscosity by Monaghan ([Monaghan1992](@cite), [Monaghan1989](@cite)).

See [`Viscosity`](@ref viscosity_sph) for an overview and comparison of implemented viscosity models.

# Keywords

  * `alpha`: A value of `0.02` is usually used for most simulations. For a relation with the          kinematic viscosity, see description above.
  * `beta=0.0`: A value of `0.0` works well for most fluid simulations and simulations             with shocks of moderate strength. In simulations where the Mach number can be             very high, eg. astrophysical calculation, good results can be obtained by             choosing a value of `beta=2.0` and `alpha=1.0`.
  * `epsilon=0.01`: Parameter to prevent singularities.
