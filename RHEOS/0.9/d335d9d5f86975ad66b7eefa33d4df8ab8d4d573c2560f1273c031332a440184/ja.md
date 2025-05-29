```
modelpredict(data::RheoTimeData, model::RheoModelClass; diff_method="BD", kwargs...)
```

`RheoModelClass` とパラメータ値を受け取る `modelpredict` のバリエーション。これは、すでに作成されたモデルではなく、異なるパラメータ値の大規模なスクリーニングが必要な場合に分析を迅速化します。モデル予測の目的のために、関連する弾性率関数のみが作成されます。
