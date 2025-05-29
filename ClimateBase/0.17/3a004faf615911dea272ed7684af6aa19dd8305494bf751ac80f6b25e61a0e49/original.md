```
interpolate_pressure2height(A::ClimArray,heights::Vector; extrapolation_bc=NaN)
```

Return a `ClimArray` where the vertical coordinate is height above ground. Height above ground is calculated with the `pressure2height` function, based on hydrostatic equilibrium, and then interpolated to the given heights.

`A`: ClimArray with pressure [Pa] as height coordinate. `heights`: Vector which contains the heights that `A` should be interpolated on in meters above ground. `extrapolation_bc`: Extrapolation is set to `NaN` by default, but can be any value or linear extrapolation with `extrapolation_bc = Line()`. For other extrapolation methods use the `Interpolations` package.
