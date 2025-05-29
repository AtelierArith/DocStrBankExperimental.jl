```
azeotrope_pressure(model::EoSModel, T; v0 = x0_azeotrope_pressure(model,T))
```

は、指定された温度でのアジオトロープ圧力と特性を計算します。次の要素を含むタプルを返します：

  * アジオトロープ圧力 `[Pa]`
  * アジオトロープ点での液体体積 [`m³`]
  * アジオトロープ点での蒸気体積 [`m³`]
  * アジオトロープ組成
