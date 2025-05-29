```
OptimizationAM(; kwargs...)
```

最適化関数をOptimization.jlライブラリを使用して最大化します。

選択された最適化アルゴリズムに応じて、`x`に対する制約を処理できます。

# キーワード

  * `algorithm::Any`: 最適化アルゴリズムを定義します。
  * `multistart::Union{<:Int, <:AbstractMatrix{<:Real}}`: 最適化の再起動の回数、または列としての最適化初期点の行列。
  * `parallel::Bool`: `parallel=true`の場合、個々の再起動が並行して実行されます。
  * `autodiff:SciMLBase.AbstractADType:`: `Optimization.OptimizationFunction`に渡される自動微分モジュール。
  * `kwargs...`: その他のキーワード引数は最適化アルゴリズムに渡されます。
