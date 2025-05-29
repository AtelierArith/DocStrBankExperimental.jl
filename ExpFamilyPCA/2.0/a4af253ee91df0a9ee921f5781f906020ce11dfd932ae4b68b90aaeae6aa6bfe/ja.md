```
BernoulliEPCA(indim::Integer, outdim::Integer; options = Options(μ = 0.5))
```

ベルヌーイEPCA。

# 引数

  * `indim::Integer`: 入力空間の次元。
  * `outdim::Integer`: 潜在（出力）空間の次元。
  * `options::Options`: オプションのパラメータ（デフォルト: `μ = 0.5`）。

# 戻り値

  * `epca`: ベルヌーイ分布のための`EPCA`サブタイプ。
