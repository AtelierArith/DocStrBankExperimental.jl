```
SpatialExponential()
```

空間指数共分散構造。繰り返し効果のみに使用されます。

$$
R_{i,j} = \sigma^{2} * exp(-dist(i,j)/\theta)
$$

ここで `dist` は、被験者 `i` と `j` の繰り返し効果行列の行ベクトル間のユークリッド距離であり、θ > 0 です。

SPEXP = SpatialExponential()
