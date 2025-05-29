```
iterate(nn, ics)
```

初期条件 `ics` に対して [`TransformerIntegrator`](@ref) 型のニューラルネットワークを反復します。

初期条件は、行列 $\in\mathbb{R}^{n\times\mathtt{seq\_length}}$ または 2 つの行列の `NamedTuple` です。

この関数は、評価目的のためにすでに訓練された Transformer の軌道を計算します。

# パラメータ

以下はオプションのキーワード引数です：

  * `n_points::Int=100`: 予測を実行する時間ステップの数。
  * `prediction_window::Int=size(ics.q, 2)`: 予測ウィンドウ（すなわち、未来に予測するステップの数）は、デフォルトでシーケンスの長さ（すなわち、入力時間ステップの数）に等しいです。
