```
SourceParameters
```

Custom type defining the source parameters of a Fourier spectrum.

Constructed with signature `SourceParameters{S<:Float64, T<:Real}` with fields:

  * `Δσ::T` is the stress parameter in bars
  * `RΘϕ::S` is the radiation pattern
  * `V::S` is the partition factor (for splitting to horizontal components)
  * `F::S` is the free surface factor
  * `β::S` is the source velocity in units of km/s
  * `ρ::S` is the source density in units of t/m³ or g/cm³
  * `model::Symbol` identifies the type of source spectrum (`:Brune`, `:Atkinson_Silva_2000`)
