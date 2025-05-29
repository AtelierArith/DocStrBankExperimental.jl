```
pm,vs,vl = melting_temperature(model::CompositeModel,T;v0=x0_melting_pressure(model,T))
```

指定された圧力で固体と流体相のEoSを含む`CompositeModel`の融解温度を計算します。体積の初期値のタプル`(vs0,vl0)`を渡すことができます。

返すもの:

  * 融解温度 [`K`]
  * 指定された圧力での融解固体体積 [`m³`]
  * 指定された圧力での融解液体体積 [`m³`]
