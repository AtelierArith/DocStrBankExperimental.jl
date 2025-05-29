```
round(a::Interval[, RoundingMode])
```

整数の制限に丸められた区間を返します。

IEEE Std 1788-2015に準拠するために、「roundTiesToEven」は`round(a)`または`round(a, RoundNearest)`に対応し、「roundTiesToAway」は`round(a, RoundNearestTiesAway)`に対応します。
