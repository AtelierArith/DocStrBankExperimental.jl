```
shortestcovint(bsamp::MixedModelFitCollection, level = 0.95)
```

`bsamp.allpars` の各パラメータに対して `level` 比率を含む最短区間を返します。

!!! warning
    現在、系統的にゼロの相関が結果に含まれています。これは将来のリリースで変更される可能性がありますが、破壊的変更とは見なされません。

