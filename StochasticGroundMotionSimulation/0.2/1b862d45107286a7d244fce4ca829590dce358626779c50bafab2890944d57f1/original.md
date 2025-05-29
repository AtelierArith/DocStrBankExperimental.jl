```
fourier_path(f::U, r_ps::T, m::S, geo::GeometricSpreadingParameters, sat::NearSourceSaturationParameters, ane::AnelasticAttenuationParameters) where {S<:Real,T<:Real,U<:Float64}
```

Path scaling of Fourier spectral model – combination of geometric spreading and anelastic attenuation.

See also: [`geometric_spreading`](@ref), [`anelastic_attenuation`](@ref)
