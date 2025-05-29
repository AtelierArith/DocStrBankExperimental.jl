```
GLMNetClassifier(;resampling=StratifiedCV(), params...)
```

`glmnetcv` 関数に基づくバイナリ/多項式結果のための GLMNet 分類器です。[GLMNet.jl](https://github.com/JuliaStats/GLMNet.jl) パッケージから。

# 引数:

  * resampling: MLJ `ResamplingStrategy`、[MLJ のリサンプリング戦略](https://alan-turing-institute.github.io/MLJ.jl/dev/evaluating_model_performance/#Built-in-resampling-strategies)を参照
  * params: `glmnetcv` 関数への追加パラメータ

# 例:

`alpha=0` の glmnet。

```julia

model = GLMNetClassifier(resampling=StratifiedCV(nfolds=3), alpha=0)
mach = machine(model, X, y)
fit!(mach, verbosity=0)
```
