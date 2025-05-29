```
intensity_point(model::AbstractModel, x, y, args...)
```

モデルが画像領域 `IsAnalytic()` の特性を持っている場合に、点ごとの強度を計算する関数です。そうでない場合は、可視空間で画像を構築し、それを反転します。
