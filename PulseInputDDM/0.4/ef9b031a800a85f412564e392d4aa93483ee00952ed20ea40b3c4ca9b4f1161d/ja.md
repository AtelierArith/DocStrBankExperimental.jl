```
fit(model, options)
```

`noiseless_neuralDDM`のモデルパラメータをフィットします。

引数:

  * `model`: `noiseless_neuralDDM`のインスタンス。
  * `options`: 最適化に関連するいくつかの詳細、例えば、フィットされたパラメータ（`fit`）、およびそれらのパラメータの上限（`ub`）と下限（`lb`）。

返り値:

  * `model`: `noiseless_neuralDDM`のインスタンス。
  * `output`: [`Optim.optimize`](@ref)からの結果。
