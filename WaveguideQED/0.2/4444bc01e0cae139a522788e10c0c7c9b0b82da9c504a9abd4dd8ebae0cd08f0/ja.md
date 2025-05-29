```
absorption(b1::WaveguideBasis{T},b2::FockBasis) where T
absorption(b1::FockBasis,b2::WaveguideBasis{T}) where T
```

[`CavityWaveguideAbsorption`](@ref) を作成し、`FockBasis` に対して `create(b::FockBasis)` を適用し、[`WaveguideBasis{T}`](@ref) に対して `destroy(b::WaveguideBasis{T})` を適用します。
