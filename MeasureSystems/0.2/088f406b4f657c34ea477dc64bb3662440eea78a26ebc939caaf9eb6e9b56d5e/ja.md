```Julia
vacuumpermeability(U::UnitSystem) = 𝟏/vacuumpermittivity(U)/(lightspeed(U)*lorentz(U))^2
permeability : [FT²Q⁻²R⁻¹C²], [FT²Q⁻²], [MLQ⁻²], [𝟙], [L⁻²T²]
FT²Q⁻²R⁻¹C² [μ₀] 統一

真空中の磁気透過率は、SI単位系（H⋅m⁻¹, kg⋅m²⋅C⁻²）で `μ₀` と定義される。

```

Julia julia> vacuumpermeability(Metric) # H⋅m⁻¹ τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [H⋅m⁻¹] Metric

julia> vacuumpermeability(Conventional) # H⋅m⁻¹ 𝘤⁻¹α⋅RK90⋅2 = 1.25663703976(19) × 10⁻⁶ [H⋅m⁻¹] Conventional

julia> vacuumpermeability(CODATA) # H⋅m⁻¹ 𝘤⁻¹α⋅RK⋅2 = 1.25663706194(35) × 10⁻⁶ [H⋅m⁻¹] CODATA

julia> vacuumpermeability(SI2019) # H⋅m⁻¹ 𝘩⋅𝘤⁻¹𝘦⁻²α⋅2 = 1.25663706212(19) × 10⁻⁶ [H⋅m⁻¹] SI2019

julia> vacuumpermeability(International) # H⋅m⁻¹ Ωᵢₜ⁻¹τ⋅2⁻⁶5⁻⁷ = 1.2560153338456637×10⁻⁶ [H⋅m⁻¹] International

julia> vacuumpermeability(EMU) # abH⋅cm⁻¹ 𝟏 = 1.0 [𝟙] EMU

julia> vacuumpermeability(ESU) # statH⋅cm⁻¹ 𝘤⁻²2⁻⁴5⁻⁴ = 1.1126500560536184×10⁻²¹ [cm⁻²s²] ESU ```
