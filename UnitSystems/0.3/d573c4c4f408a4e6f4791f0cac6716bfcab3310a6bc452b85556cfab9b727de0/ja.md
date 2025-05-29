```Julia
FFF = EntropySystem(Metric,𝟐*𝟕*DAY,fur,𝟐*𝟑^2*𝟓*lb,°R,0,𝟏)
```

ファーロング–ファーキン–フォートナイト `FFF` は、珍しい非実用的な単位に基づいたユーモラスな `UnitSystem` です。

```Julia
julia> boltzmann(FFF) # fir⋅fur²⋅ftn⁻²⋅F⁻¹
6.793104372040068e-18

julia> planckreduced(FFF) # fir⋅fur²⋅ftn⁻¹⋅rad⁻¹
7.721326066522303e-35

julia> lightspeed(FFF) # fur⋅ftn⁻¹
1.8026174997852542e12

julia> vacuumpermeability(FFF) # fir⋅fur⋅Inf⁻²
0.0

julia> electronmass(FFF) # fir
2.2314170421728741e-32

julia> molarmass(FFF) # fir⋅fir-mol⁻¹
1

julia> luminousefficacy(FFF) # lm⋅ftn³⋅fir⁻¹⋅fur⁻²
6.375788993269434e-10
```
