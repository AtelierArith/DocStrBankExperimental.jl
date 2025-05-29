```
choice_neural_optimize(model, options)
```

選択と神経データを使用して `neural_choiceDDM` のモデルパラメータ（潜在的にすべて）を最適化します。

引数:

  * `model`: `neural_choiceDDM` のインスタンス。

返り値:

  * `model`: `neural_choiceDDM` のインスタンス。
  * `output`: [`Optim.optimize`](@ref) からの結果。
