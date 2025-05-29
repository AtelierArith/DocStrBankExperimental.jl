```
SampleOptAM(; kwargs...)
```

ユーザーが提供した事前分布から候補をサンプリングし、次に最も高い獲得値を持つサンプルから開始される複数の最適化実行を行うことで、獲得関数を最適化します。

# キーワード

  * `x_prior::MultivariateDistribution`: 候補をサンプリングするために使用される入力領域の事前分布。
  * `samples::Int`: 引き出され評価されるサンプルの数。
  * `algorithm::Any`: 最適化アルゴリズムを定義します。
  * `multistart::Int`: 最適化の再起動の数。
  * `parallel::Bool`: `parallel=true`の場合、サンプリングと個々の最適化実行が並行して行われます。
  * `autodiff:SciMLBase.AbstractADType:`: `Optimization.OptimizationFunction`に渡される自動微分モジュール。
  * `kwargs...`: 他のキーワード引数は最適化アルゴリズムに渡されます。
