```
pressure_drop(f::Fluid, t::Tube[; friction])
```

流体が特定の摩擦を持つチューブを流れるときの圧力降下を計算します。

詳細については、VDI Heat Atlasのp. 1057を参照してください。

# 引数

  * `f::Fluid`: チューブを流れる流体
  * `t::Tube`: 流体が流れるチューブ

# キーワード

  * `friction::Float`: チューブを流れる流体の摩擦係数

# 戻り値

  * `DynamicQuantities.AbstractQuantity`: チューブを流れる流体の圧力降下
