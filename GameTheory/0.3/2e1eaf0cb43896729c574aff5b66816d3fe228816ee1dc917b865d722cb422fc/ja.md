```
StochasticFictitiousPlay(g, d[, gain=DecreasingGain()])
```

`StochasticFictitiousPlay` インスタンスを構築します。

# 引数

  * `g::NormalFormGame` : `NormalFormGame` インスタンス。
  * `d::Distributions.Distribution` : 利得の摂動が引き出される `Distribution` インスタンス。
  * `gain::AbstractGain` : 利得またはステップサイズを指定する引数；`DecreasingGain()` または `ConstantGain(size)`。

# 戻り値

  * `::StochasticFictitiousPlay` : 確率的擬似プレイモデル。
