```
assess(
    sys::PSY.System,
    aggregation::Type{AT},
    method::PRASCore.SequentialMonteCarlo,
    resultsspecs::PRASCore.Results.ResultSpec...,
) where {AT <: PSY.AggregationTopology}
```

モンテカルロシミュレーションを使用してリソースの適合性を分析します。

# 引数

  * `sys::PSY.System`: PowerSystems.jl システムモデル
  * `aggregation::Type{AT}`: PRAS に変換する際に使用する集約トポロジー
  * `method::PRASCore.SequentialMonteCarlo`: 使用するシミュレーション方法
  * `resultsspec::PRASCore.Results.ResultSpec...`: 計算する結果

# 戻り値

  * `resultsspec` からの結果のタプル: デフォルトは ([`ShortfallResult`](@ref),)
