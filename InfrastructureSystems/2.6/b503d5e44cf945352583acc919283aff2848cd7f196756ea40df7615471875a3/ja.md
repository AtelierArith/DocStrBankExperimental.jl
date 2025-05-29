```
mutable struct DeterministicSingleTimeSeries <: AbstractDeterministic
    single_time_series::SingleTimeSeries
    initial_timestamp::Dates.DateTime
    interval::Dates.Period
    count::Int
    horizon::Int
end
```

既存の [`SingleTimeSeries`](@ref) をラップする決定論的予測

`DeterministicSingleTimeSeries` は、各初期時刻にウィンドウを保存する代わりに、増加するオフセットで既存の `SingleTimeSeries` へのビューを提供するため、[`Deterministic`](@ref) とまったく同じように動作します。これにより、予測間の重複ウィンドウがある場合に大規模なデータの重複を回避できます。

実際の予測データが利用できない場合、過去のデータに基づいた完璧な予測として使用できます。

# 引数

  * `single_time_series::SingleTimeSeries`: ラップされた `SingleTimeSeries` オブジェクト
  * `initial_timestamp::Dates.DateTime`: 時系列の利用可能な時間
  * `interval::Dates.Period`: 予測ウィンドウ間の時間ステップ
  * `count::Int`: 予測ウィンドウの数
  * `horizon::Int`: この時系列の長さ
