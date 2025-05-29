```Julia
gaussgravitation(U::UnitSystem) = sqrt(gravitation(U)*solarmass(U)/astronomicalunit(U)^3)
angularfrequency : [T⁻¹A], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
T⁻¹A⋅(𝘤⁻¹R∞⁻¹α²kG⋅2⁻¹⁵3⁻⁷5⁻⁵ = 2.56456351221(79) × 10⁻²⁸) [ħ⁻¹𝘤²mₑ⋅g₀⁻¹] 統一

```

ガウス重力定数 `k` ニュートンの法則 (Hz または rad⋅D⁻¹)。

```Julia
julia> gaussgravitation(Engineering)
kG⋅τ⋅2⁻¹⁴3⁻⁷5⁻⁵ = 1.990983676471466×10⁻⁷ [s⁻¹rad] 工学

julia> gaussgravitation(MetricGradian)
kG⋅2⁻¹⁰3⁻⁷5⁻³ = 1.2674995749028348×10⁻⁵ [s⁻¹gon] メトリックグラディアン

julia> gaussgravitation(MetricDegree)
kG⋅2⁻¹¹3⁻⁵5⁻⁴ = 1.1407496174125516×10⁻⁵ [s⁻¹deg] メトリック度

julia> gaussgravitation(MetricArcminute)
kG⋅2⁻⁹3⁻⁴5⁻³ = 0.0006844497704475308 [s⁻¹amin] メトリックアークミニッツ

julia> gaussgravitation(MetricArcsecond)
kG⋅2⁻⁷3⁻³5⁻² = 0.041066986226851857 [s⁻¹asec] メトリックアークセカンド

juila> gaussgravitation(MPH)
kG⋅τ⋅2⁻¹⁰3⁻⁵5⁻³ = 0.0007167541235297278 [h⁻¹] MPH

julia> gaussgravitation(IAU)
kG⋅τ⋅2⁻⁷3⁻⁴5⁻³ = 0.017202098964713464 [D⁻¹] IAU☉
```
