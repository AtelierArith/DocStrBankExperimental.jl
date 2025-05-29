```
geometric_spreading(r_ps::T, m::S, geo::GeometricSpreadingParameters, sat::NearSourceSaturationParameters) where {S<:Real, T<:Real}
```

Geometric spreading function, switches between different approaches on `path.geo_model`.
