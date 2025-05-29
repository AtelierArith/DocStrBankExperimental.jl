```
compute_virial_pressure(sol::OZSolution, system::SimpleLiquid)
```

圧力をビリアル経路を通じて計算します

単一成分系の場合の式は p = kBTρ - 1/(2d) ρ^2 ∫dr r g(r) u'(r) であり、混合物の場合は p = kBT Σᵢρᵢ - 1/(2d) Σᵢⱼ ρᵢρⱼ ∫dr r gᵢⱼ(r) u'ᵢⱼ(r) です。

`discontinuities(potential)` が定義されている場合、相互作用ポテンシャルの不連続性を解析的に処理します。追加の速度/精度のために、du/drを解析的に計算する `evaluate_potential_derivative(potential, r::Number)` のメソッドを定義してください。デフォルトでは、これは有限差分を使用して行われます。
