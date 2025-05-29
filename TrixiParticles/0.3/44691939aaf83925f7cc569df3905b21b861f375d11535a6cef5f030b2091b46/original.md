```
ViscosityMorris(; nu, epsilon=0.01)
```

Viscosity by [Morris (1997)](@cite Morris1997) also used by [Fourtakas (2019)](@cite Fourtakas2019).

See [`Viscosity`](@ref viscosity_sph) for an overview and comparison of implemented viscosity models.

# Keywords

  * `nu`: Kinematic viscosity
  * `epsilon=0.01`: Parameter to prevent singularities
