```
cverror(model::GeoStatsModel, geotable, method; kwargs...)
```

与えられた `geotable` に対して、ジオスタティスティカル `model` の交差検証誤差を、`kwargs` に応じて `Interpolate` または `InterpolateNeighbors` を使用して、誤差推定 `method` で推定します。

```
cverror(model::StatsLearnModel, geotable, method)
cverror((model, feats => targs), geotable, method)
```

与えられた `geotable` に対して、統計学習 `model` の交差検証誤差を、誤差推定 `method` で推定します。
