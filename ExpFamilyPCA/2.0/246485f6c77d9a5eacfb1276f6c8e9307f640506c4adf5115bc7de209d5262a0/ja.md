```
ContinuousBernoulliEPCA(indim::Integer, outdim::Integer; options::Options = Options(μ = 0.5))
```

連続ベルヌーイEPCA。

# 引数

  * `indim::Integer`: 入力空間の次元。
  * `outdim::Integer`: 潜在（出力）空間の次元。
  * `options::Options`: オプションのパラメータ（デフォルト: `μ = 0.25`）。

# 戻り値

  * `epca`: 連続ベルヌーイ分布のための`EPCA`サブタイプ。
