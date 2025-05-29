```
pseudoabsencemask(::Type{SurfaceRangeEnvelope}, presences::SDMLayer{Bool})
```

擬似欠如を引き出すためのマスクを生成します。これは、(i) 出現のバウンディングボックス内にあり、(ii) レイヤーに値があり、(iii) すでに出現によって占有されていないセルを選択することによって行われます。
