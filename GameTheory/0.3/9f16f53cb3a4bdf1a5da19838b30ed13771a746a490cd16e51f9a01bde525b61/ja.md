```
FictitiousPlay(g[, gain=DecreasingGain()])
```

`NormalFormGame`から`FictitiousPlay`インスタンスを構築します。

# 引数

  * `g::NormalFormGame` : `NormalFormGame`インスタンス。
  * `gain::AbstractGain` : 利得またはステップサイズを指定する引数；`DecreasingGain()`または`ConstantGain(size)`。

# 戻り値

  * `::FictitiousPlay` : フィクティシャスプレイモデル。
