```
acentric_factor(model::EoSModel;crit = crit_pure(model), satmethod = ChemPotVSaturation())
```

は、その定義を使用してアセントリック因子を計算します：

```
ω = -log10(psatᵣ) -1, at Tᵣ = 0.7
```

そのために、臨界温度を計算し（`crit_pure`を使用）、飽和計算を実行します（`saturation_pressure(model,0.7Tc,satmethod)`を使用）。
