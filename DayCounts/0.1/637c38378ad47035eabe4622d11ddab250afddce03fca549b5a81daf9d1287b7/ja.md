```
yearfrac(startdate::Date, enddate::Date, dc::DayCount)
```

`startdate` と `enddate` の間の年数の小数部分を、[`DayCount` オブジェクト](@ref daycount_types) `dc` に従って計算します。

  * `startdate == enddate` の場合、結果はゼロです。
  * `startdate > enddate` の場合、結果は `-yearfrac(enddate, startdate, dc)` です。
