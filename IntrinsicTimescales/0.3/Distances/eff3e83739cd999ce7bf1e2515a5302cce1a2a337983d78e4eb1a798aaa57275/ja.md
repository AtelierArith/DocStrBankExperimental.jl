```
linear_distance(data, synth_data)
```

要約統計量間の平均二乗（L2）距離を計算します。

# 引数

  * `data::Union{AbstractArray, Real}`: 観測データの要約統計量
  * `synth_data::Union{AbstractArray, Real}`: シミュレーションデータの要約統計量

# 戻り値

  * `Float64`: データとsynth_dataの間の平均二乗差

# 注意事項

  * スカラーおよび配列入力の両方を処理します
  * 配列の場合、平均化する前に要素ごとの差を計算します
  * 線形スケールでの要約統計量の比較に便利です
