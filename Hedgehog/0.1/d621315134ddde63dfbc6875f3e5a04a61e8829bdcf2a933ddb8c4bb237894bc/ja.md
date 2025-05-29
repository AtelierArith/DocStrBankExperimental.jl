```
add_yearfrac(t::TimeType, yf::Real) -> DateTime
```

`Date` または `DateTime` `t` に小数年数 (`yf`, ACT/365 として計算) を加えます。

`t` を Julia `Dates` モジュールのエポックからのミリ秒に変換し、`yf` に対応する期間を加算し、結果を `DateTime` オブジェクトに戻します。
