```
dEds(::Type{<:BetheEnergyLoss}, e::Float64, elm::Element, ρ::Float64; mip::Type{<:NeXLMeanIonizationPotential}=Berger1982)
dEds(::Type{<:BetheEnergyLoss}, e::Float64, mat::Material, inclDensity=true; mip::Type{<:NeXLMeanIonizationPotential}=Berger1982)
```

Calculate the loss per unit path length for an electron in the specified element and density.  The results in energy loss in eV/cm.  Implemented by `Type{Bethe}` and `Type{JoyLuo}`.
