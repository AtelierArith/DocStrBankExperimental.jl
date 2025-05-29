```
StochasticFictitiousPlay(fp[, d=fp.d, gain=fp.gain])
```

`fp`から新しい`StochasticFictitiousPlay`インスタンスを構築します。

# 引数

  * `fp::AbstractFictitiousPlay` : `AbstractFictitiousPlay`インスタンス。
  * `d::Distributions.Distribution` : 利得の摂動が引き出される`Distribution`インスタンス。
  * `gain::AbstractGain` : 利得またはステップサイズを指定する引数。

# 戻り値

  * `::StochasticFictitiousPlay` : 確率的虚構プレイモデル。
