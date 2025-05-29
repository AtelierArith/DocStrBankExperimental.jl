```
Alfven_speed(B::BField, ρ)
Alfven_speed(𝐁::Vector{BField}, ρ)
Alfven_speed(B::BField, n::NumberDensity, mass_number = 1)
Alfven_speed(𝐁::Vector{BField}, n::NumberDensity, mass_number = 1)
```

アルフヴェン速度 $V_A$ は、準中性プラズマにおける磁気擾乱の典型的な伝播速度です。

これはアルフヴェン速度とは異なることに注意してください。詳細は [`Alfven_velocity`](@ref) を参照してください。参考文献: [PlasmaPy API Documentation](https://docs.plasmapy.org/en/stable/api/plasmapy.formulary.speeds.Alfven_speed.html)
