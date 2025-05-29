```Julia
electronvolt(U::UnitSystem) = elementarycharge(U)*volt(U)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(𝘩⁻¹𝘤⁻¹𝘦⋅R∞⁻¹α²2⁻¹ = 1.95695118356(60) × 10⁻⁶) [𝘤²mₑ⋅g₀⁻¹] 統一

真空中で1ボルトによって加速された静止電子が得る`energy`の単位（Jまたはlb⋅ft）。

```

Julia julia> electronvolt(SI2019) # J 𝘦 = 1.602176634×10⁻¹⁹ [J] SI2019

julia> electronvolt(SI2019)/lightspeed(SI2019) # kg⋅m⋅s⁻¹ 𝘤⁻¹𝘦 = 5.344285992678308×10⁻²⁸ [N⋅s] SI2019

julia> electronvolt(SI2019)/lightspeed(SI2019)^2 # kg 𝘤⁻²𝘦 = 1.7826619216278975×10⁻³⁶ [kg] SI2019

julia> electronvolt(SI2019)/planck(SI2019)/lightspeed(SI2019) # m⁻¹ 𝘩⁻¹𝘤⁻¹𝘦 = 806554.393734921 [m⁻¹] SI2019

julia> electronvolt(SI2019)/boltzmann(SI2019) # K kB⁻¹𝘦 = 11604.518121550082 [K] SI2019 ```
