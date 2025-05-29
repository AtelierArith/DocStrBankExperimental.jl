```Julia
hubble(U::UnitSystem) = time(U,Hubble)
frequency : [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
T⁻¹⋅(𝘤⁻¹R∞⁻¹α²H0⋅au⁻¹2⁻¹¹3⁻⁴5⁻⁶ = 2.824(18) × 10⁻³⁹) [ħ⁻¹𝘤²mₑ⋅ϕ⁻¹g₀⁻¹] 統一

```

ハッブル宇宙膨張周波数パラメータ。

```Julia
julia> hubble(Metric)
H0⋅au⁻¹τ⋅2⁻¹⁰3⁻⁴5⁻⁶ = 2.193(14) × 10⁻¹⁸ [Hz] メトリック

julia> hubble(Hubble)
𝟏 = 1.0 [T⁻¹] ハッブル

julia> hubble(Cosmological)
ΩΛ⁻¹ᐟ²τ¹ᐟ²2⋅3⁻¹ᐟ² = 3.487(14) [T⁻¹] 宇宙論的

julia> 𝟏/hubble(Metric)/year(Metric)
H0⁻¹aⱼ⁻¹au⋅τ⁻¹2³3⋅5⁴ = 1.4452(90) × 10¹⁰ [𝟙] メトリック
```
