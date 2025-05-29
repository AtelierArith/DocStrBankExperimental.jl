```
logarithmic_distance(data, synth_data)
```

対数の要約統計量間の平均二乗距離を計算します。

# 引数

  * `data::Union{AbstractArray, Real}`: 観測データの要約統計量
  * `synth_data::Union{AbstractArray, Real}`: シミュレーションデータの要約統計量

# 戻り値

  * `Float64`: log(data) と log(synth_data) の間の平均二乗差

# 注意事項

  * スカラーおよび配列入力の両方を処理します
  * 配列の場合、平均化する前に要素ごとの対数差を計算します
  * 複数のオーダーの大きさにわたる要約統計量を比較するのに便利です
  * すべての値が正であると仮定します
