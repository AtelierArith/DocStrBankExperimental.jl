```
LinearEquationOfState([FT=Float64;] thermal_expansion=1.67e-4, haline_contraction=7.80e-4)
```

Return `LinearEquationOfState` for `SeawaterBuoyancy` with `thermal_expansion` coefficient and `haline_contraction` coefficient. The buoyancy perturbation $b$ for `LinearEquationOfState` is

$$
    b = g (α T - β S),
$$

where $g$ is gravitational acceleration, $α$ is `thermal_expansion`, $β$ is `haline_contraction`, $T$ is temperature, and $S$ is practical salinity units.

Default constants in units inverse Kelvin and practical salinity units for `thermal_expansion` and `haline_contraction`, respectively, are taken from Table 1.2 (page 33) of Vallis, "Atmospheric and Oceanic Fluid Dynamics: Fundamentals and Large-Scale Circulation" (2nd ed, 2017).
