```
pv(rate::Real, nper::Integer, pmt::Real, fv = 0.0, when = :end)
```

将来価値 `fv`、利率 `rate`、および一定の定期支払い `pmt` を、期間数 `nper` にわたって考慮して現在価値を計算します。支払いは、`when` 引数で指定されたように、各期間の開始 (`:begin`) または終了 (`:end`) に行われることが期待されます。
