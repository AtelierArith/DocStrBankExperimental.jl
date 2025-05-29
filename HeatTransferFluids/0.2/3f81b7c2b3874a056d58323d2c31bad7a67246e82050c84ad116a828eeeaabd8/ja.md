```
heat_transfer(f::Fluid, t::Tube)
```

流体がチューブを流れるときの熱伝達係数を計算します。

# 引数

  * `f::Fluid`: チューブを流れる流体
  * `t::Tube`: 流体が流れるチューブ

# 戻り値

  * `DynamicQuantity.AbstractQuantity`: チューブを流れる流体の熱伝達係数
