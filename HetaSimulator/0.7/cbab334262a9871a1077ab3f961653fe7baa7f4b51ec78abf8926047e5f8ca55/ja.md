```
function estimator(
  platform::Platform,
  parameters_fitted;
  scenarios::Union{AbstractVector{Symbol}, Nothing} = nothing, # all if nothing
  kwargs... 
)
```

パラメータの特定と分析のための尤度推定器関数を生成します。これはPlatformのインターフェースです。詳細は基本の`estimator`メソッドを参照してください。

引数:

  * `platform` : [`Platform`](@ref)型のプラットフォーム
  * `parameters_fitted` : 最適化パラメータとその初期値
  * `scenarios` : `Symbol`型のシナリオ識別子のベクター。デフォルトは`nothing`
  * `kwargs...` : `estimator`がサポートする他の引数、基本メソッドを参照してください。
