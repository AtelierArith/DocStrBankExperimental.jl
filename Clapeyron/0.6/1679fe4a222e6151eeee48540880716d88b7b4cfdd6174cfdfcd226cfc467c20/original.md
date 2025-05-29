```
VT_mechanical_stability(model,V,T,z = SA[1.0])::Bool
```

Performs a mechanical stability for a (V,T,z) pair, returns `true/false`. Checks if isothermal compressibility is not negative.

!!! note
    This function does not have a `p`,`T` counterpart, because if we calculate the volume via `volume(model,p,T,z)`, it will be, by definition, a mechanically stable phase.

