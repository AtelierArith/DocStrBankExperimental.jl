```
nper(rate::Real, pmt::Real, pv::Real, fv = 0.0, when = :end)
```

特定の利率 `rate` と固定支払い `pmt` に基づいて、現在価値 `pv` が将来価値 `fv` に達するまでの期間数を計算します。支払いは、`when` 引数で指定されたように、各期間の開始 (`:begin`) または終了 (`:end`) に行われることが期待されます。
