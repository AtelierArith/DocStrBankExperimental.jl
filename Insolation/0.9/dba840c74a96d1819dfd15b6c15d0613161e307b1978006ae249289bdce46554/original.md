```
orbital_params(od::OrbitalData, dt::FT) where {FT <: Real}
```

Parameters are interpolated from the values given in the Laskar 2004 dataset using a cubic spline interpolation.

See [`OrbitalData`](@ref).
