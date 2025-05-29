```Julia
gaussgravitation(U::UnitSystem) = sqrt(gravitation(U)*solarmass(U)/astronomicalunit(U)^3)
angularfrequency : [T⁻¹A], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
T⁻¹A⋅(𝘤⁻¹R∞⁻¹α²kG⋅2⁻¹⁵3⁻⁷5⁻⁵ = 2.56456351221(79) × 10⁻²⁸) [ħ⁻¹𝘤²mₑ⋅g₀⁻¹] Unified
```

Gaussian  gravitational constant `k` of Newton's laws (Hz or rad⋅D⁻¹).

```Julia
julia> gaussgravitation(Engineering)
kG⋅τ⋅2⁻¹⁴3⁻⁷5⁻⁵ = 1.990983676471466×10⁻⁷ [s⁻¹rad] Engineering

julia> gaussgravitation(MetricGradian)
kG⋅2⁻¹⁰3⁻⁷5⁻³ = 1.2674995749028348×10⁻⁵ [s⁻¹gon] MetricGradian

julia> gaussgravitation(MetricDegree)
kG⋅2⁻¹¹3⁻⁵5⁻⁴ = 1.1407496174125516×10⁻⁵ [s⁻¹deg] MetricDegree

julia> gaussgravitation(MetricArcminute)
kG⋅2⁻⁹3⁻⁴5⁻³ = 0.0006844497704475308 [s⁻¹amin] MetricArcminute

julia> gaussgravitation(MetricArcsecond)
kG⋅2⁻⁷3⁻³5⁻² = 0.041066986226851857 [s⁻¹asec] MetricArcsecond

juila> gaussgravitation(MPH)
kG⋅τ⋅2⁻¹⁰3⁻⁵5⁻³ = 0.0007167541235297278 [h⁻¹] MPH

julia> gaussgravitation(IAU)
kG⋅τ⋅2⁻⁷3⁻⁴5⁻³ = 0.017202098964713464 [D⁻¹] IAU☉
```
