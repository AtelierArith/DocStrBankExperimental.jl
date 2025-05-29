```
customthresunder(C::ClimGrid, thres)
```

customthresunder、指定された閾値未満の日数の年間数。

TS[i,j]を年jのi日目のデイリータイムシリーズ値とします。次の条件を満たす日数をカウントします：

TS[i,j] < thres。
