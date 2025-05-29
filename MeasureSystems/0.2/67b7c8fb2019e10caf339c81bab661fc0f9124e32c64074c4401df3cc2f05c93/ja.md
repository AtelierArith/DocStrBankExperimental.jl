```Julia
pound(U::UnitSystem) = mass(𝟏,U,English)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²lb⋅2⁻¹ = 4.9793969039(15) × 10²⁹) [mₑ] 統一

English `pound` 単位の `mass` (kg または lb)。

```

Julia julia> pound(Metric) # kg lb = 0.45359237 [kg] メトリック

julia> pound(CGS) # g lb⋅2³5³ = 453.59237 [g] ガウス

julia> pound(English) # lb 𝟏 = 1.0 [lbm] 英語

julia> pound(British) # slug g₀⁻¹ft = 0.031080950171567256 [slug] ブリティッシュ

julia> pound(Gravitational) # hyl g₀⁻¹lb = 0.046253549377208325 [hyl] 重力 ```
