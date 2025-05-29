```
LLE_pressure(model::EoSModel, T, x; v0 = x0_LLE_pressure(model,T,x))
```

は、与えられた温度での液-液平衡圧力と特性を計算します。

次の要素を含むタプルを返します：

  * LLE圧力 `[Pa]`
  * LLE点での組成 `x₁ = x` の液体体積 [`m³`]
  * LLE点での組成 `x₂` の液体体積 [`m³`]
  * 液体組成 `x₂`
