```
emission(b1::WaveguideBasis{T},b2::FockBasis) where T
emission(b1::FockBasis,b2::WaveguideBasis{T}) where T
```

[`CavityWaveguideEmission`](@ref) を作成し、`FockBasis` に対して `destroy(b::FockBasis)` を適用し、[`WaveguideBasis{T}`](@ref) に対して `create(b::WaveguideBasis{T})` を作成します。
