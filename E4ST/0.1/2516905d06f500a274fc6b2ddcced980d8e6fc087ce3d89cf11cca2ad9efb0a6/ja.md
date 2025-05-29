```
get_pgen_bus(data, model, bus_idx, year_idx, hour_idx)
```

バスの特定の時間における総発電量を返します。     * モデルが最適化された後に変数の値を取得するために、この関数をvalue()でラップします。次のようにします: value.(get*pgen*bus)。
