```
BSpline(degree)
```

Bスプラインカーネル。`degree` は `Linear()`, `Quadratic()` または `Cubic()` のいずれかです。

!!! warning
    `BSpline(Quadratic())` と `BSpline(Cubic())` は境界を正しく処理できません。なぜなら、カーネル値が単に切り捨てられるため、不安定な動作を引き起こすからです。したがって、境界の適切な処理が必要な場合は、`SteffenBSpline` または `KernelCorrection` のいずれかを使用することをお勧めします。

