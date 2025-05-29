```
Tt,pt,vs,vl,vv = triple_point(model::CompositeModel;v0 = x0_triple_point(model))
```

`CompositeModel`の固体および流体相EoSを含む三重点を計算します。

返すもの：

  * 三重点温度 [`K`]
  * 三重点圧力 [`Pa`]
  * 三重点における固体体積 [`m³`]
  * 三重点における液体体積 [`m³`]
  * 三重点における蒸気体積 [`m³`]
