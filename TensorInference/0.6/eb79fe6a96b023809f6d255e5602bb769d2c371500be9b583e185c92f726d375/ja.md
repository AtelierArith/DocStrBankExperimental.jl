```julia
TensorNetworkModel(
    model::TensorInference.UAIModel{ET, FT};
    openvars,
    evidence,
    optimizer,
    simplifier,
    unity_tensors_labels
) -> TensorInference.TensorNetworkModel{OMEinsum.DynamicNestedEinsum{Int64}}

```

### キーワード引数

  * `openvars` は出力に残る変数のリストです。空でない場合、返り値は非ゼロランクのテンソルになります。
  * `evidence` は証拠の辞書で、値は0からカウントを始める整数です。
  * `optimizer` はテンソルネットワーク収束順序の最適化器で、利用可能なアルゴリズムについてはパッケージ [`OMEinsumContractionOrders.jl`](https://github.com/TensorBFS/OMEinsumContractionOrders.jl) を確認してください。
  * `simplifier` は `optimizer` を高速化するためのいくつかの戦略で、上記のリンクを参照してください。
  * `unity_tensors_labels` はユニティテンソルのラベルのリストです。デフォルトではすべて単一の変数、すなわち `[[1], [2], ..., [n]]` です。複数の変数を指定することもでき、計算の複雑さが増す可能性があります。
