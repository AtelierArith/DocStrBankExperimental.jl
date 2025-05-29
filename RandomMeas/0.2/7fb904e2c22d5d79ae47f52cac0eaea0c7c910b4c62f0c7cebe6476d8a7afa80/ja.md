```
get_purity(group::Measurementgroup, subsystem::Vector{Int} = collect(1:group.N))
```

測定データから量子状態の純度を計算するために、測定結果の重なりを平均化します。

# 引数

  * `group::MeasurementGroup`: ランダム化された測定の結果と設定を含む測定データ。
  * `subsystem::Vector{Int}` (オプション): 保持するサブシステムを指定するサイトインデックスのベクトル。デフォルトは全システムです。

# 戻り値

  * 指定されたサブシステムの計算された純度。
