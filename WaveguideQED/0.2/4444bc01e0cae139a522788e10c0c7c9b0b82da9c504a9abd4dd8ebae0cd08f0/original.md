```
absorption(b1::WaveguideBasis{T},b2::FockBasis) where T
absorption(b1::FockBasis,b2::WaveguideBasis{T}) where T
```

Create [`CavityWaveguideAbsorption`](@ref) that applies `create(b::FockBasis)` on `FockBasis` and destroy(b::WaveguideBasis{T}) on [`WaveguideBasis{T}`](@ref).  
