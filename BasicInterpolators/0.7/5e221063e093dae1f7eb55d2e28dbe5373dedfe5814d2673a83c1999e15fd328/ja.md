```
CubicSplineInterpolator(x, y, dy₁, dyₙ, boundaries=StrictBoundaries())
```

座標 `x` と値 `y` で定義された点のための `CubicSplineInterpolator` を構築します。このコンストラクタは、境界での一階導関数が `dy₁` と `dyₙ` によって設定されるクランプスプラインを作成します。
