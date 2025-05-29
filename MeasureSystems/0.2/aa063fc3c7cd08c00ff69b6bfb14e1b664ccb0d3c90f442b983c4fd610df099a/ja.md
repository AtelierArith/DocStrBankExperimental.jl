```Julia
luminousefficacy(U::UnitSystem) = Kcd*power(U)
luminousefficacy(U::UnitSystem{𝟏}) = 𝟏
luminousefficacy : [F⁻¹L⁻¹TJ], [F⁻¹L⁻¹TJ], [M⁻¹L⁻²T³J], [M⁻¹L⁻²T³J], [M⁻¹L⁻²T³J]
F⁻¹L⁻¹TJ [Kcd] Unified
```

540 THzの単色放射の光束効率`Kcd`（lm⋅W⁻¹）。

```Julia
julia> luminousefficacy(Metric) # lm⋅W⁻¹
Kcd = 683.01969009009 [lm⋅W⁻¹] Metric

julia> luminousefficacy(CODATA) # lm⋅W⁻¹
𝘩⋅Kcd⋅RK⋅KJ²2⁻² = 683.0197015(85) [lm⋅W⁻¹] CODATA

julia> luminousefficacy(Conventional) # lm⋅W⁻¹
𝘩⋅Kcd⋅RK90⋅KJ90²2⁻² = 683.0198236454071 [lm⋅W⁻¹] Conventional

julia> luminousefficacy(International) # lm⋅W⁻¹
Kcd⋅Ωᵢₜ⁻¹Vᵢₜ² = 683.1324069249656 [lm⋅W⁻¹] International

julia> luminousefficacy(British) # lm⋅s³⋅slug⋅ft⁻²
Kcd⋅g₀⋅ft⋅lb = 926.0503548878947 [lb⁻¹ft⁻¹s⋅lm] British
```
