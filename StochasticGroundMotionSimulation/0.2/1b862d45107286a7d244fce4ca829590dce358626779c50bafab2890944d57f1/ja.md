```
fourier_path(f::U, r_ps::T, m::S, geo::GeometricSpreadingParameters, sat::NearSourceSaturationParameters, ane::AnelasticAttenuationParameters) where {S<:Real,T<:Real,U<:Float64}
```

フーリエスペクトルモデルのパススケーリング - 幾何学的広がりと非弾性減衰の組み合わせ。

参照: [`geometric_spreading`](@ref), [`anelastic_attenuation`](@ref)
