```
ParetoEPCA(indim::Integer, outdim::Integer, m::Real; options::Options = Options(μ = 2, A_init_value = 2, A_lower = 1 / indim, V_init_value = -2, V_upper = -1))
```

パレートEPCA。

# 引数

  * `indim::Integer`: 入力空間の次元。
  * `outdim::Integer`: 潜在（出力）空間の次元。
  * `m::Real`: サポート内の最小値を表すパレート分布の既知のパラメータ。
  * `options::Options`: モデル初期化のためのオプションパラメータ：

      * `μ`: デフォルト値 `2`。
      * `A_init_value`: 行列 `A` の初期値（デフォルト: `2`）。
      * `A_lower`: 行列 `A` の下限（デフォルト: `1 / indim`）。
      * `V_init_value`: 行列 `V` の初期値（デフォルト: `-2`）。
      * `V_upper`: 行列 `V` の上限（デフォルト: `-1`）。

# 戻り値

  * `epca`: パレート分布のための `EPCA` サブタイプ。
