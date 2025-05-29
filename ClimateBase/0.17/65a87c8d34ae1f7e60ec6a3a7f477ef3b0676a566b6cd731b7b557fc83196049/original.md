```
interpolate_height2pressure(A::ClimArray, pressure_levels::Vector; extrapolation_bc=NaN )
```

Return a `ClimArray` where the vertical coordinate is pressure. Pressure levels are calculated with the `height2pressure` function, based on hydrostatic equilibrium, and then interpolated to the given levels.

`A`: `ClimArray` with height above ground [m] as height coordinate. `pressure_levels`: Vector which contains the pressure levels in Pascal that `A` should be interpolated on. `extrapolation_bc`: Extrapolation is set to `NaN` by default, but can be any value or linear extrapolation with `extrapolation_bc = Line()`. For other extrapolation methods use the `Interpolations` package.
