```julia
MaterialOptimizationProblem(ψ, test, u₀, ps, adb, loss)

```

`Optimization.jl`（[https://docs.sciml.ai/Optimization/stable/](https://docs.sciml.ai/Optimization/stable/)）で最適なパラメータを見つけるために使用する`OptimizationProblem`を作成します。

# 引数:

  * `ψ`: 使用する材料モデル
  * `test`または`tests`: パラメータをフィッティングする際に使用する`::AbstractMaterialTest`の単一またはベクトル
  * `u₀`: パラメータの初期推測
  * `ps`: `predict()`を呼び出すための追加のパラメータ
  * `adb`: [`ADTypes.jl`](https://github.com/SciML/ADTypes.jl)から微分タイプを選択します。このタイプは、`OptimizationProblem`に適用されるADのタイプにも自動的に適用されます。
  * `loss`: [`LossFunctions.jl`](https://github.com/JuliaML/LossFunctions.jl)からの損失関数
