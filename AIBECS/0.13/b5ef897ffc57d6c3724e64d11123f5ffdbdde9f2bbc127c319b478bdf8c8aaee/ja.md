```
RatioAtStation(x, y, grd, station, depthlims=(0,Inf))
```

クルーズトラック `ct` に沿ったトレーサー `x` の緯度経度断面をプロットします。

キーワード引数 `zlims=(ztop, zbottom)` を指定することで、深さ `z ∈ (ztop, zbottom)` のみをプロットすることができます。 （この場合、`z` は下向きに正です）
