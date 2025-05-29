```Julia
josephson(U::UnitSystem) = 𝟐*elementarycharge(U)*lorentz(U)/planck(U)
```

ジョセフソン定数 `KJ` は、電位差と照射周波数 (Hz⋅V⁻¹) を関連付けます。

```Julia
julia> josephson(SI2019) # Hz⋅V⁻¹
4.835978484169836e14

julia> josephson(Metric) # Hz⋅V⁻¹
4.835978485488147e14

julia> josephson(Conventional) # Hz⋅V⁻¹
4.8359789999999994e14

julia> josephson(CODATA) # Hz⋅V⁻¹
4.8359785250000006e14

julia> josephson(International) # Hz⋅V⁻¹
4.8375743583883575e14

julia> josephson(EMU) # Hz⋅abV⁻¹
4.835978485488148e6

julia> josephson(ESU) # Hz⋅statV⁻¹
1.4497898769996093e17
```
