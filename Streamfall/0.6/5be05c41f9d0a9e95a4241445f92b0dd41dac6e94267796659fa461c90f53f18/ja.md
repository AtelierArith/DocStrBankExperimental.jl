```
calibrate!(ensemble::WeightedEnsembleNode, climate::Climate, calib_data::Union{AbstractArray,DataFrame}, metric::Union{F,AbstractDict{String,F}}; kwargs...) where {F}
```

個々のアンサンブルの重みをキャリブレーションし、コンポーネントモデルが事前にキャリブレーションされていると仮定します。

# 引数

  * `ensemble`: 複数のモデルインスタンスを含むWeightedEnsembleNode
  * `climate`: シミュレーション用の気候データ
  * `calib_data`: ノード名を列として持つ配列またはDataFrameとしてのキャリブレーションデータ
  * `metric`: 最適化メトリック関数またはノード名をメトリックにマッピングするDict
  * `kwargs`: BlackBoxOptimに渡される追加の引数

# 戻り値

  * 重みのキャリブレーションからの(最適化*結果, 最適化*セットアップ)のタプル
