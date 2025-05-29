```
compute_ρ_sfc(thermo_params, ts_in, T_sfc)
```

Computes the density of air at the surface, given the temperature at the surface T*sfc, the thermodynamic state of the atmosphere, ts*in, and a set of Clima.Thermodynamics parameters thermo_params.

This assumes the ideal gas law and hydrostatic balance to extrapolate to the surface.
