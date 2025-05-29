```
yearfrac(start, stop)
```

2つの時点間のACT/365年の分数を計算します。

入力の`start`と`stop`は、`Date`、`DateTime`、またはティック（`Int`または`Float64`）であることができます。ティックが提供される場合、それらはJuliaの`Dates`モジュールのエポック（0000-01-01T00:00:00）からのミリ秒であると見なされ、`to_ticks`の出力と一致します。
