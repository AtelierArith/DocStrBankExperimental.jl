```
inertial_waveform(inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
inertial_waveform(inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

与えられた `inspiral` 出力によって [`orbital_evolution`](@ref) で、慣性系におけるポストニュートン波形モードの重みを評価します。

慣性系は慣性観測者が存在する系であるため、この波形は実際の観測者が検出する波形に近いものです。この関数は、PN式が提供される共軸系から波形を変換します。

他の引数と返される量の詳細については、[`coorbital_waveform`](@ref) を参照してください。
