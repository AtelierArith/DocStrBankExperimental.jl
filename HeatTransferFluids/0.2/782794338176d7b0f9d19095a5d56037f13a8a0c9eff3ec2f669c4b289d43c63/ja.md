```
pressure_drop(f::Fluid, h::Helix)
```

流体がヘリックスを通過する際の圧力降下を計算します。

# 引数

  * `f::Fluid`: チューブを流れる流体
  * `h::Helix`: 流体が流れるヘリックス

# 戻り値

  * `DynamicQuantity.AbstractQuantity`: チューブを流れる流体の圧力降下
