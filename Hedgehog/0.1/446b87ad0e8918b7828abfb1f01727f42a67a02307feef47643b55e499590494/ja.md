```
to_ticks(x::Date)
```

`Date`をJuliaの`Dates`モジュールのエポック（0000-01-01）からのミリ秒に変換します。

注意: これは、`Date`をエポックからの日数に変換し（`Dates.date2epochdays`）、それに`MILLISECONDS_IN_DAY`を掛けることで計算されます。
