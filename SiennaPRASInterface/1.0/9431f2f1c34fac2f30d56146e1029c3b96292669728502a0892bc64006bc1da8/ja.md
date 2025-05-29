```julia
assess(
    sys::PowerSystems.System,
    template::SiennaPRASInterface.RATemplate,
    method::PRASCore.Simulations.SequentialMonteCarlo,
    resultsspecs::PRASCore.Results.ResultSpec...
) -> Any

```

モンテカルロシミュレーションを使用してリソースの適合性を分析します。

# 引数

  * `sys::PSY.System`: PowerSystems.jl システムモデル
  * `template::RATemplate`: PRAS 問題テンプレート
  * `method::PRASCore.SequentialMonteCarlo`: 使用するシミュレーション方法
  * `resultsspec::PRASCore.Results.ResultSpec...`: 計算する結果

# 戻り値

  * `resultsspec` からの結果のタプル: デフォルトは ([`ShortfallResult`](@ref),)
