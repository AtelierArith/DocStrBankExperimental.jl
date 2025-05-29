```
GaussianEPCA(indim::Integer, outdim::Integer; options::Options = Options())
```

ガウス損失を持つEPCAモデル。

# 引数

  * `indim::Integer`: 入力空間の次元。
  * `outdim::Integer`: 潜在（出力）空間の次元。
  * `options::Options`: オプションのパラメータ。

# 戻り値

  * `epca`: ガウス分布のためのEPCAサブタイプ。
