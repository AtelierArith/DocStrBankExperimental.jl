```
pm,vs,vl = sublimation_temperature(model::CompositeModel,T;v0=x0_sublimation_pressure(model,T))
```

指定された圧力で固体と流体相のEoSを含む`CompositeModel`の昇華温度を計算します。体積の初期値のタプル`(vs0,vl0)`を渡すことができます。

返されるもの:

  * 昇華温度 [`K`]
  * 指定された圧力での昇華固体体積 [`m³`]
  * 指定された圧力での昇華蒸気体積 [`m³`]
