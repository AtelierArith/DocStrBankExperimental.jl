```
UCEP_mix(model::EoSModel;v0=x0_UCEP_mix(model))
```

バイナリ混合物の上部臨界終点を計算します。

返すもの：

  * UCEP温度 [`K`]
  * UCEP圧力 [`Pa`]
  * UCEP点での液体体積 [`m³`]
  * UCEP点での蒸気体積 [`m³`]
  * UCEP点での液体モル組成
  * UCEP点での蒸気モル組成
