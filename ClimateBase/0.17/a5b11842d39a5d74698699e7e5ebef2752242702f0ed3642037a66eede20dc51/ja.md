```
spacemean(A::ClimArray [, W]) = spaceagg(mean, A, W)
```

`A`の空間座標にわたって平均を計算します。オプションで`W`に統計的重みを提供できます。
