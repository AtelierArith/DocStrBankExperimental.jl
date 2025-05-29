```
scale_constraints!(constraint_list::Vector{ConstraintRef}, scaling_settings::ScalingSettings=ScalingSettings())
```

モデル `EP` のすべての制約の係数とRHSをスケーリング設定 `scaling_settings` を使用してスケーリングします。この関数は、`constraint_list` の各制約に対して `scale_constraint!(con_ref, scaling_settings)` を呼び出します。
