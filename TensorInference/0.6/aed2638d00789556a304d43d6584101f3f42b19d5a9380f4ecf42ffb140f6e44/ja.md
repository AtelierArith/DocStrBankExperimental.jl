```julia
TensorNetworkModel(
    problem::ProblemReductions.ConstraintSatisfactionProblem,
    β::Real;
    evidence,
    optimizer,
    openvars,
    simplifier,
    unity_tensors_labels
) -> TensorInference.TensorNetworkModel{OMEinsum.DynamicNestedEinsum{Int64}}

```

制約充足問題（またはエネルギーモデル）を確率モデルに変換します。

### 引数

  * `problem` は [`ProblemReductions`](https://github.com/GiggleLiu/ProblemReductions.jl) の `ConstraintSatisfactionProblem` インスタンスです。
  * `β` は逆温度です。

### キーワード引数

  * `evidence` は変数をその値にマッピングする辞書です。
  * `optimizer` はテンソルネットワークを最適化するために使用される最適化手法です。
  * `openvars` は周辺化される変数のリストです。
  * `mars` は周辺化される変数のリストです。
