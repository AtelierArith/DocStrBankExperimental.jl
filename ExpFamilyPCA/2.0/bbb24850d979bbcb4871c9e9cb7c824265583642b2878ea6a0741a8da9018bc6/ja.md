```
WeibullEPCA(indim::Integer, outdim::Integer; options::Options = Options(A_init_value = -1, A_upper = -eps(), V_lower = eps()))
```

ワイブルEPCA。

# 引数

  * `indim::Integer`: 入力空間の次元。
  * `outdim::Integer`: 潜在（出力）空間の次元。
  * `options::Options`: モデル初期化のためのオプションパラメータ。デフォルトは `NegativeDomain()`。

# 戻り値

  * `epca`: ワイブル分布のための `EPCA` サブタイプ。
