```julia
assess(
    sys::PowerSystems.System,
    method::PRASCore.Simulations.SequentialMonteCarlo,
    resultsspecs::PRASCore.Results.ResultSpec...
) -> Any

```

モンテカルロシミュレーションを使用してリソースの適合性を分析します。

エリアレベルの集約を使用したデフォルトテンプレート。

# 引数

  * `sys::PSY.System`: PowerSystems.jl システムモデル
  * `method::PRASCore.SequentialMonteCarlo`: 使用するシミュレーション方法
  * `resultsspec::PRASCore.Results.ResultSpec...`: 計算する結果

# 戻り値

  * `resultsspec` からの結果のタプル: デフォルトは ([`ShortfallResult`](@ref),)
