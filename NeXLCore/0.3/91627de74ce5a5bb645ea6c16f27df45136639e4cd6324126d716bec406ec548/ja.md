```
dEds(::Type{<:BetheEnergyLoss}, e::Float64, elm::Element, ρ::Float64; mip::Type{<:NeXLMeanIonizationPotential}=Berger1982)
dEds(::Type{<:BetheEnergyLoss}, e::Float64, mat::Material, inclDensity=true; mip::Type{<:NeXLMeanIonizationPotential}=Berger1982)
```

指定された元素と密度における電子の単位経路長あたりの損失を計算します。結果はエネルギー損失をeV/Åで示します。`Type{Bethe}`および`Type{JoyLuo}`によって実装されています。
