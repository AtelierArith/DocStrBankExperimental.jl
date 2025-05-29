```Julia
rydberg(U::UnitSystem) = hartree(U)/2planck(U)/lightspeed(U) # Eₕ/2𝘩/𝘤
```

ライデberg定数 `R∞` は、基底状態の原子をイオン化することができる最低エネルギーの光子（m⁻¹）です。

```Julia
julia> rydberg(Metric) # m⁻¹
1.0973731568160104e7
```

水素のライデberg定数 `RH` は `R∞*mₚ/(mₑ+mₚ)`（m⁻¹）です。

```Julia
julia> rydberg(Metric)*protonmass(Metric)/(electronmass(Metric)+protonmass(Metric)) # m⁻¹
1.0967758340280434e7
```

ライデberg光子エネルギー単位 `Ry` は `𝘩*𝘤*R∞` または `Eₕ/2`（J）です。

```Julia
julia> hartree(Metric)/2 # J
2.1798723611036055e-18

julia> hartree(SI2019)/𝟐/elementarycharge(SI2019) # eV
13.605693122994362
```

ライデberg光子周波数 `𝘤*R∞` または `Eₕ/2𝘩`（Hz）です。

```Julia
julia> lightspeed(Metric)*rydberg(Metric) # Hz
3.289841960250912e15
```

ライデberg波長 `1/R∞`（m）です。

```Julia
julia> 𝟏/rydberg(Metric) # m
9.112670505823788e-8

julia> 𝟏/rydberg(Metric)/τ # m⋅rad⁻¹
1.4503265557695781e-8
```

ライデberg定数の精密測定は、相対標準不確かさが10¹²の2部未満であり、他の物理定数の値を制約するために選ばれています。
