```
fscore(M::ConfusionMatrix, β=1.0)
```

Fᵦ スコアは、精度と再現率の間の調和平均として定義され、再現率の精度に対する相対的重要性を示す正の因子 β を使用します：

$$
(1 + \beta^2)\times\frac{PPV\times TPR}{(\beta^2 \times PPV) + TPR}
$$
