```
get_overlap(
    group_1::MeasurementGroup,
    group_2::MeasurementGroup,
    subsystem::Vector{Int} = collect(1:group_1.N);
    apply_bias_correction::Bool = false
)
```

2つの量子状態の重なりを測定データから計算し、測定結果の重なりを平均化します。

# 引数

  * `group_1::MeasurementGroup`: 最初の状態の測定データ。
  * `group_2::MeasurementGroup`: 2番目の状態の測定データ。
  * `subsystem::Vector{Int}` (オプション): 保持するサブシステムを指定するサイトインデックスのベクトル。デフォルトは全システムです。
  * `apply_bias_correction::Bool` (オプション): 重なりに対してバイアス補正を適用するかどうか。デフォルトは `false` です。

# 戻り値

  * 計算された重なり（または `group_1 == group_2` でバイアス補正が適用された場合は純度）。
