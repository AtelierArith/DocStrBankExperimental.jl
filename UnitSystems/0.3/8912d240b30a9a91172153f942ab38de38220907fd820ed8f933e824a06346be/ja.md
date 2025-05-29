```Julia
MPH = EntropySystem(FPS,HOUR,mi,𝟏)
```

`FPS` 絶対 `UnitSystem` に基づくマイルポンド時間仕様。

```Julia
julia> boltzmann(MPH) # lbf⋅mi²⋅hr⁻²⋅F⁻¹
8.46159564836783e-23

julia> planckreduced(MPH) # lbf⋅mi²⋅hr⁻¹⋅rad⁻¹
3.2315817800735083e-37

julia> lightspeed(MPH) # mi⋅hr⁻¹
6.706166293843951e8

julia> vacuumpermeability(MPH) # lbm⋅mi⋅C⁻²
1.72145327108138e-9

julia> electronmass(MPH) # lbm
2.0082753379555867e-30

julia> molarmass(MPH) # lbm⋅lb-mol⁻¹
1.0

julia> luminousefficacy(MPH) # lm⋅h³⋅lb⁻¹⋅mi⁻²
0.017198446999173198
```
