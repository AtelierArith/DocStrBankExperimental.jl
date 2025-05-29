```julia
update_temperature(
    tnet::TensorInference.TensorNetworkModel,
    problem::ProblemReductions.ConstraintSatisfactionProblem,
    β::Real
) -> TensorInference.TensorNetworkModel

```

テンソネットワークモデルの温度を更新します。プログラムは、収束順序を繰り返し最適化することなく、問題からテンソルを再生成します。

### 引数

  * `tnet` は [`TensorNetworkModel`](@ref) インスタンスです。
  * `problem` はターゲット制約充足問題です。
  * `β` は逆温度です。
