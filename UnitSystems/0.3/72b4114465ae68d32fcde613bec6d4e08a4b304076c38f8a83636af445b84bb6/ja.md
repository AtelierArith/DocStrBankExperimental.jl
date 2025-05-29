```Julia
hartree(U::UnitSystem) = electronmass(U)/gravity(U)*(lightspeed(U)*finestructure(U))^2
```

水素原子の基底状態におけるハートリー電位エネルギー `Eₕ` は `2R∞*𝘩*𝘤` (J) です。

```Julia
julia> hartree(SI2019)/elementarycharge(SI2019) # eV
27.211386245988724

julia> hartree(Metric) # J
4.359744722207211e-18

julia> hartree(CGS) # erg
4.359744722207211e-11

julia> hartree(Metric)*avogadro(Metric)/kilo # kJ⋅mol⁻¹
2625.499640382392

julia> hartree(Metric)*avogadro(Metric)/kilocalorie(Metric) # kcal⋅mol⁻¹
627.099203436231

julia> 𝟐*rydberg(CGS) # Eₕ/𝘩/𝘤/100 cm⁻¹
219474.63136320215

julia> hartree(Metric)/planck(Metric) # Hz
6.579683920501824e15

julia> hartree(Metric)/boltzmann(Metric) # K
315775.02491262055
```

`4π*ε₀ == 1` のガウス単位系では、ハートリーエネルギーは `𝘦^2/a₀` です。
