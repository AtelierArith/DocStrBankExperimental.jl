```
compute_inface_extreme_point(lmo, direction, x; lazy, kwargs...)
```

現在の固定によって定義された面上で、`direction` において最小化する頂点を計算するLMOのような操作。固定はオラクルによって維持される（または `x` 自体から推測される）。
