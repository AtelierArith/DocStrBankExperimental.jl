```
ChainState(model, rng::AbstractRNG=Random.default_rng())
```

これは `Lux.Chain` に似ていますが、状態を持つコンテナにラップされています。

## フィールド

  * `model`: ニューラルネットワーク。
  * `states`: ニューラルネットワークの状態。

## 入力

  * `x`: ニューラルネットワークへの入力。
  * `ps`: ニューラルネットワークのパラメータ。

## 引数

  * `model`: `AbstractExplicitLayer`、またはそれらの名前付きタプルで、`Chain` として扱われます。
  * `rng`: ニューラルネットワークの初期化に使用する `AbstractRNG`。
