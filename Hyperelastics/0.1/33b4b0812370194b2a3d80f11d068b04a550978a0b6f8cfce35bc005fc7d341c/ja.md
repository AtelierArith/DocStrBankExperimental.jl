`OptimizationProblem`を作成して、最適なパラメータを見つけるために[`Optimization.jl`](https://docs.sciml.ai/Optimization/stable/)で使用します。

# 引数:

  * `ψ`: 使用する材料モデル
  * `test`または`tests`: パラメータをフィッティングする際に使用する単一またはベクトルのハイパーエラステスト
  * `u₀`: パラメータの初期推定
  * `ps`: predictを呼び出すための追加パラメータ
  * `adb`: [`ADTypes.jl`](https://github.com/SciML/ADTypes.jl)から微分タイプを選択します。このタイプは、Optimization Problemに適用されるADのタイプにも自動的に適用されます。
  * `loss`: [`LossFunctions.jl`](https://github.com/JuliaML/LossFunctions.jl)からの損失関数
