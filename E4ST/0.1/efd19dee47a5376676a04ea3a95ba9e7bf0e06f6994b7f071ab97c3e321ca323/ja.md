```
add_pl_gs_bus!(config, data, model)
```

モデルに発電基準を満たす負荷電力である `pl_gs_bus` 式を追加します。これには以下が含まれます：

  * 名目負荷から制限された負荷を引いたもの `plnom_bus - plcurt_bus`
  * バッテリー損失（すなわち、充電と放電の差）
  * 線損失
