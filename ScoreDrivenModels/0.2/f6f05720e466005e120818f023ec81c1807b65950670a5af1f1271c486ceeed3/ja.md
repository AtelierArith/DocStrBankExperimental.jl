```
forecast(series::Vector{T}, gas::ScoreDrivenModel{D, T}, H::Int; kwargs...) where {D, T}
```

時間系列の将来の値の予測分位数を、GAS再帰を `H` 回更新し、Blasques, Francisco, Siem Jan Koopman, Katarzyna Lasak, Andre Lucas (2016) の方法に従ってモンテカルロ法を使用して行います: "In-Sample Confidence Bounds and Out-of-Sample Forecast Bands for Time-Varying Parameters in Observation Driven Models", International Journal of Forecasting, 32(3), 875-887。

希望する分位数を `Vector{T}` として渡すことができます。デフォルトの動作は中央値と `0.025` および `0.975` の分位数を予測することです。

デフォルトでは1000のシナリオが使用されますが、`S` キーワード引数を切り替えることで変更できます。

デフォルトでは、このメソッドはスコア駆動再帰を実行するために `stationary_initial_params` メソッドを使用します。異なる `initial_params` のセットでモデルを推定した場合は、ここでそれらを使用して推定の一貫性を維持してください。
