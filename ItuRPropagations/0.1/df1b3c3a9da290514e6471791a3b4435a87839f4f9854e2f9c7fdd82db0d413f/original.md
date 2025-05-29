```
linkparameters(latlon::LatLon, f::Real, p::Real, θ::Real, D::Real; η::Real=60.0, hs::Union{Real,Missing}=missing, polarization::IturEnum=EnumCircularPolarization)
```

Link parameters for link budget. Includes cloud, gaseous, rain, scintillation, and total attenuations; space station noise temperature,     earth station noise temperature, and cross-polarization discrimination.

# Arguments

  * `latlon::LatLon`: latitude and longitude (degrees)
  * `f::Real`: frequency (GHz)
  * `p::Real`: exceedance probability (%)
  * `θ::Real`: elevation angle (degrees)
  * `D::Real`: antenna diameter (m)
  * `η::Real=60`: antenna efficiency (% from 0 to 100, typically 60)
  * `hs::Union{Real,Missing}=missing`: altitude of ground station (km)
  * `polarization::IturEnum=EnumCircularPolarization`: polarization (EnumHorizontalPolarization, EnumVerticalPolarization, or EnumCircularPolarization)

# Return

  * `(Ac=Ac, Ag=Ag, Ar=Ar, As=As, At=At)`: cloud, gas, rain, scintillation, total attenuations (dB)
