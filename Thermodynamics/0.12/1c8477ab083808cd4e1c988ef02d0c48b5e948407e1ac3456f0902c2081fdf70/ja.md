```
q_vap_saturation_generic(param_set, T, ρ[, phase=Liquid()])
```

平面表面の凝縮物に対する飽和比湿を計算します。次の情報が必要です。

```
- `param_set`: `AbstractParameterSet`、詳細については[`Thermodynamics`](@ref)を参照してください
- `T`: 温度
- `ρ`: 空気密度
- (オプション) `Liquid()`: 凝縮物が液体であることを示します
- (オプション) `Ice()`: 凝縮物が氷であることを示します
```
