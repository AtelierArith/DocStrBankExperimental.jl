```
scale_constraints!(EP::Model, scaling_settings::ScalingSettings=ScalingSettings())
```

モデル `EP` のすべての制約の係数と右辺をスケーリング設定 `scaling_settings` を使用してスケーリングします。この関数は `EP` のすべての制約の配列を作成し、その後配列に対して scale*constraint!(con*ref, scaling_settings) をブロードキャストします。
