```
customthresover(C::ClimGrid, thres)
```

customthresover、指定された閾値を超える年間の日数。

TS[i,j]を年jのi日目のデイリータイムシリーズ値とします。次の条件を満たす日数をカウントします：

TS[i,j] > thres。
