```
inventory = co2_inventory(model, ws, states, t; cells = missing, co2_name = "CO2")
inventory = co2_inventory(model, result::ReservoirSimResult; cells = missing)
```

与えられた `model`、井戸の結果 `ws` および報告時間 t に対して、各ステップの CO2 在庫を計算します。提供されている場合、キーワード引数 `cells` は、セルによって定義された領域内の在庫を計算し、追加の CO2 を「領域外」として分類します。

在庫は、各エントリがその時点での CO2 の状態の内訳を含む辞書のベクターになります。これには、残留トラッピングおよび溶解トラッピングが含まれます。
