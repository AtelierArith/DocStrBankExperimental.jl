```
BinomialEPCA(indim::Integer, outdim::Integer, n::Integer; options::Options = Options(μ = 0.5))
```

二項EPCA。

# 引数

  * `indim::Integer`: 入力空間の次元。
  * `outdim::Integer`: 潜在（出力）空間の次元。
  * `n::Integer`: 試行回数を表す既知のパラメータ（非負）。
  * `options::Options`: オプションのパラメータ（デフォルト: `μ = 0.5`）。

# 戻り値

  * `epca`: 二項分布のための`EPCA`サブタイプ。
