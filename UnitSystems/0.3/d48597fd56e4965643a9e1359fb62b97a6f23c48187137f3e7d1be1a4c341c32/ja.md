```Julia
vacuumimpedance(U::UnitSystem) = vacuumpermeability(U)*lightspeed(U)*rationalization(U)*lorentz(U)^2
```

真空インピーダンス `Z₀` は電場と磁場の大きさの比率 (Ω) です。

```Julia
julia> vacuumimpedance(Metric) # Ω
376.73031346177066

julia> vacuumimpedance(Conventional) # Ω
376.7303069637538

julia> vacuumimpedance(CODATA) # Ω
376.730313611642

julia> vacuumimpedance(SI2019) # Ω
376.73031366716776

julia> vacuumimpedance(International) # Ω
376.5439242192822

julia> vacuumimpedance(InternationalMean) # Ω
376.5458060168224

julia> 120π # 3e8*μ₀ # Ω
376.99111843077515

julia> vacuumimpedance(EMU) # abΩ
3.767303134617706e11

julia> vacuumimpedance(ESU) # statΩ
4.191690043903362e-10

julia> vacuumimpedance(HLU) # hlΩ
3.335640951981521e-11

julia> vacuumimpedance(IPS) # in⋅lb⋅s⋅C⁻²
3334.3442363371373
```
