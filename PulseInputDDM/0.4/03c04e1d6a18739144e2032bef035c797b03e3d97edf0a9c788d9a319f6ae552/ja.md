```
choice_optimize(model, options)
```

選択データを使用して `neural_choiceDDM` の選択関連モデルパラメータを最適化します。

引数:

  * `model`: `neural_choiceDDM` のインスタンス。

戻り値:

  * `model`: `neural_choiceDDM` のインスタンス。
  * `output`: [`Optim.optimize`](@ref) からの結果。

```
