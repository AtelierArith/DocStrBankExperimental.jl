```Julia
Nautical = EntropySystem(Metric,HOUR,nm,em^3,𝟏,τ*𝟑^3/𝟐^10/𝟓^12,milli)
```

海里、キロ地球グラム、`Meridian` 定義に基づく時間仕様。

```Julia
julia> greatcircle(Nautical) # nm
21600.0

julia> boltzmann(Nautical) # keg⋅nm²⋅hr⁻²⋅K⁻¹
5.180046617683878e-23

julia> planckreduced(Nautical) # keg⋅nm²⋅hr⁻¹⋅rad⁻¹
1.0990666907335472e-37

julia> lightspeed(Nautical) # nm⋅hr⁻¹
5.819538375927914e8

julia> vacuumpermeability(Nautical) # keg⋅nm⋅eC⁻²
6.785840131753953e-10

julia> electronmass(Nautical) # keg
9.06992538542115e-31

julia> molarmass(Nautical) # keg⋅eg-mol⁻¹
0.001

julia> luminousefficacy(Nautical) # lm⋅h³⋅keg⁻¹⋅nm⁻²
0.050568530951469015
```
