```
FluxApproximator(; model, optimiser, usegpu=false)
```

強化学習のための `FluxApproximator` オブジェクトを構築します。

# 引数

  * `model`: 近似に使用されるモデル。
  * `optimiser`: モデルを更新するために使用されるオプティマイザ。
  * `usegpu`: 計算にGPUを使用するかどうかを示すブール値。デフォルトは `false`。

# 戻り値

`FluxApproximator` オブジェクト。
