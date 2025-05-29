```
channel(::Type{Float64}, eV::AbstractFloat, sc::EnergyScale)::Float64
```

Returns the fractional-channel index of the specified energy X-ray (in eV).

```
channel(eV::AbstractFloat, sc::EnergyScale)::Int
channel(eV::Float64, spec::Spectrum)::Int
channel(eV::Float64, det::EDSDetector)::Int
```

Returns the integer index of the channel for the specified energy X-ray (in eV).
