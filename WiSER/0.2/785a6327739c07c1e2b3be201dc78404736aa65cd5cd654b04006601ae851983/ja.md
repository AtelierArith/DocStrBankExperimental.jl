```
rand!(m::WSVarLmmModel; respdist = MvNormal, γωdist = MvNormal, Σγω = [], kwargs...)
```

モデルオブジェクトのデータ `X, Z, W` 行列に基づいて、シミュレートされた応答に `m.data[i].y` の応答を置き換えます。

  * モデルオブジェクトのデータ `X, Z, W` 行列のデータ。
  * モデル内のパラメータ値。
  * ランダム効果に与えられた応答の共分布分布。
  * ランダム効果の分布。
  * MvTDistribution からシミュレートする場合は、`df = x` を介して自由度を指定する必要があります。
