```
GLMNetRegressor(;resampling=CV(), params...)
```

`glmnetcv` 関数に基づく連続的な結果のための GLMNet 回帰器で、[GLMNet.jl](https://github.com/JuliaStats/GLMNet.jl) パッケージから提供されています。

# 引数:

  * resampling: MLJ `ResamplingStrategy`、[MLJ のリサンプリング戦略](https://alan-turing-institute.github.io/MLJ.jl/dev/evaluating_model_performance/#Built-in-resampling-strategies)を参照
  * params: `glmnetcv` 関数への追加パラメータ

# 例:

`alpha=0` の glmnet。

```julia

model = GLMNetRegressor(resampling=CV(nfolds=3), alpha=0)
mach = machine(model, X, y)
fit!(mach, verbosity=0)
```
