```Julia
rpm(U::UnitSystem) = turn(U)/minute(U)
angularfrequency : [T⁻¹A], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
T⁻¹A⋅(𝘤⁻¹R∞⁻¹α²2⁻³3⁻¹5⁻¹ = 1.34888329905(41) × 10⁻²²) [ħ⁻¹𝘤²mₑ⋅g₀⁻¹] Unified
```

Revolutions per minute `rpm` unit of `angularfrequency` (rad⋅s⁻¹).

```Julia
julia> rpm(Engineering) # rad⋅s⁻¹
τ⋅2⁻²3⁻¹5⁻¹ = 0.10471975511965977 [s⁻¹rad] Engineering

julia> rpm(MetricGradian) # gon⋅s⁻¹
2²3⁻¹5 = 6.666666666666666 [s⁻¹gon] MetricGradian

julia> rpm(MetricDegree) # deg⋅s⁻¹
2⋅3 = 6.0 [s⁻¹deg] MetricDegree

julia> rpm(MetricArcminute) # amin⋅s⁻¹
2³3²5 = 360.0 [s⁻¹amin] MetricArcminute

julia> rpm(MetricArcsecond) # asec⋅s⁻¹
2⁵3³5² = 21600.0 [s⁻¹asec] MetricArcsecond

julia> rpm(MPH) # rad⋅h⁻¹
τ⋅2²3⋅5 = 376.99111843077515 [h⁻¹] MPH

julia> rpm(IAU) # rad⋅D⁻¹
τ⋅2⁵3²5 = 9047.786842338604 [D⁻¹] IAU☉
```
