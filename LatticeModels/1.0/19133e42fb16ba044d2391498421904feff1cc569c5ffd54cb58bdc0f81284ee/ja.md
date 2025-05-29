```
PointFlux(flux, [point; gauge])
```

与えられたフラックスとポイントを使用して `PointFlux` オブジェクトを構築します。

オプションの `gauge` 引数は、フィールドのゲージを指定するために使用できます。可能な値は `:axial` ($A(r) = B \times \frac{r}{|r|}$) と `:singular` （粒子がポイントの下を通過すると位相が変化します）です。デフォルトは `:axial` です。
