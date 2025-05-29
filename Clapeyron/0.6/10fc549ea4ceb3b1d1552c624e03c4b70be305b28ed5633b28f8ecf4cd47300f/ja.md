```
psub,vs,vv = sublimation_pressure(model::CompositeModel,T;v0=x0_sublimation_pressure(model,T))
```

指定された圧力で、固体および流体相のEoSを含む`CompositeModel`の昇華圧を計算します。体積の初期値のタプル`(vs0,vv0)`を渡すことができます。

返されるもの:

  * 昇華圧 [`Pa`]
  * 指定された温度での昇華固体体積 [`m³`]
  * 指定された温度での昇華蒸気体積 [`m³`]
