```julia
struct GeneratorStatusDA <: FullNetworkSystems.GeneratorStatus
```

デイアヘッドの定式化に必要な発電機の状態時系列データ。

フィールド:

  * `hours_at_status::AxisKeys.KeyedArray{Float64, 1}`: 各発電機がその日の開始時に現在のコミットメント状態にあった時間
  * `availability::AxisKeys.KeyedArray{Bool, 2}`: 各時間に発電機がコミット可能であるかを示すフラグ
  * `must_run::AxisKeys.KeyedArray{Bool, 2}`: 各時間に発電機がコミットしなければならないかを示すフラグ
