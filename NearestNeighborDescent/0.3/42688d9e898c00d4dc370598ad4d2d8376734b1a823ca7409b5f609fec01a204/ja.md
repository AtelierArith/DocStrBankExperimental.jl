```
nndescent(GraphT::Type{ApproximateKNNGraph}, data, n_neighbors, metric; kwargs...)
```

`data`内の各点の近似近傍を見つけるために、`GraphT`型のKNNグラフを反復的に洗練させます。最終的なKNNグラフを返します。

# キーワード引数

  * `max_iters = 10`: 候補近傍を洗練させるための反復回数の上限を設定します。高い値は速度と精度のトレードオフになります。進展がほとんどない場合、グラフ構築は早期に終了することがあります。
  * `sample_rate = 1`: 各点の周りの*ローカルジョイン*を計算するためのサンプルレートです。低い値は速度と精度のトレードオフになります。
  * `precision = 1e-3`: 早期終了のための閾値であり、精度は「早期終了のために見逃される真のkNNの割合の大まかな値」です。低い値は時間がかかりますが、より正確な結果を返します。
