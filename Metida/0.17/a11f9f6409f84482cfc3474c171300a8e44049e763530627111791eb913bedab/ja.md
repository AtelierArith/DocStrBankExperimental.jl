```
SpatialPower()
```

空間パワー共分散構造。繰り返し効果のみに使用されます。

$$
R_{i,j} = \sigma^{2} * \rho^{dist(i,j)}
$$

ここで `dist` は、被験者 `i` と `j` の繰り返し効果行列の行ベクトル間のユークリッド距離であり、1 > ρ > -1 です。

SPPOW = SpatialPower()
