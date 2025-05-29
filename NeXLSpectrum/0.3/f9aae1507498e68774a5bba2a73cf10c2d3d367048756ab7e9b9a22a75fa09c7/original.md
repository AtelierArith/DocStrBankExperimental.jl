```
EnergyScale
```

An EnergyScale is a way of representing the energy axis associated with X-ray data. The scale may be linear, polynomial or ??? to handle the various different non-linearities that happen with EDS detectors plus we can also handle WDS wavescans.

Implements:

```
channel(::Type{Float64}, eV::AbstractFloat, sc::EnergyScale)::Float64
energy(ch::Int, sc::EnergyScale)::Float64
```
