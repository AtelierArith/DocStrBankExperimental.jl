```
geometric_spreading(r_ps::T, m::S, geo::GeometricSpreadingParameters, sat::NearSourceSaturationParameters) where {S<:Real, T<:Real}
```

幾何拡散関数で、`path.geo_model`に基づいて異なるアプローチに切り替えます。
