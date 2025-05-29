```
function estimator(
  scenarios::AbstractVector{C},
  parameters_fitted;
  kwargs...
) where {C<:AbstractScenario}
```

パラメータの特定と分析のための尤度推定器関数を生成します。これはベクトル内のシナリオのインターフェースです。詳細は基本の `estimator` メソッドを参照してください。

引数:

  * `scenarios` : [`Scenario`](@ref) 型のシナリオのベクトル
  * `parameters_fitted` : 最適化パラメータとその初期値
  * `kwargs...` : `estimator` によってサポートされる他の引数、基本メソッドを参照してください。
