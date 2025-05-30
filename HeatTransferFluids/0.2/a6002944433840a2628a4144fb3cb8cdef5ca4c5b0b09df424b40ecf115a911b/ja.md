```
pressure_drop(f::Fluid, b::Bend)
```

流体が曲がりを通過する際の圧力損失を計算します。

これまでのところ、90度の曲がりのみをサポートしています。詳細はSpedding, P.L., Bernard, E. and McNally, G.M., ‘Fluid ﬂow through 90 degree bends’, Dev. Chem. Eng Mineral Process, 12: 107–128, 2004を参照してください。

# 引数

  * `f::Fluid`: チューブを流れる流体
  * `b::Bend`: 流体が流れるバルブ

# 戻り値

  * `DynamicQuantity.AbstractQuantity`: チューブを流れる流体の圧力損失

```
