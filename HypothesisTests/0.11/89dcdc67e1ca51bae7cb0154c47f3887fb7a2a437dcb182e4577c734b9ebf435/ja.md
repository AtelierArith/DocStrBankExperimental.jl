```
DieboldMarianoTest(e1::AbstractVector{<:Real}, e2::AbstractVector{<:Real}; loss=abs2, lookahead=1)
```

ハーヴェイ、レイボーン、ニューボールドによって提案された修正されたダイボールド-マリアーノテストを実行し、2つの手法が同じ予測精度を持つという帰無仮説を検定します。`loss`は、Diebold, F.X. と Mariano, R.S. (1995) の「Comparing predictive accuracy」に記載されている損失関数であり、`lookahead`は予測の先読みステップ数です。

# 参考文献

  * Diebold, F.X. と Mariano, R.S. (1995) Comparing predictive accuracy.  Journal of Business and Economic Statistics, 13, 253-263.
  * Harvey, D., Leybourne, S., & Newbold, P. (1997). Testing the equality of prediction  mean squared errors. International Journal of forecasting, 13(2), 281-291.
