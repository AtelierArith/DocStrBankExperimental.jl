```
emission(b1::WaveguideBasis{T},b2::FockBasis) where T
emission(b1::FockBasis,b2::WaveguideBasis{T}) where T
```

Create [`CavityWaveguideEmission`](@ref) that applies `destroy(b::FockBasis)` on `FockBasis` and create(b::WaveguideBasis{T}) on [`WaveguideBasis{T}`](@ref).  
