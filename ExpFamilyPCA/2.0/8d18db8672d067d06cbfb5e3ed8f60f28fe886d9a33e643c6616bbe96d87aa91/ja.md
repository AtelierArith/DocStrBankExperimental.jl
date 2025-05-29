```
NegativeBinomialEPCA(indim::Integer, outdim::Integer, r::Integer; options::Options = Options(A_init_value = -1, A_upper = -eps(), V_lower = eps()))
```

負の二項EPCA。

# 引数

  * `indim::Integer`: 入力空間の次元。
  * `outdim::Integer`: 潜在（出力）空間の次元。
  * `r::Integer`: 成功の数（正の）を表す負の二項分布の既知のパラメータ。
  * `options::Options`: EPCAモデルのオプション設定パラメータ。 

      * `A_init_value`: 行列 `A` の初期充填値（デフォルト: `-1`）。
      * `A_upper`: 行列 `A` の上限、デフォルトは `-eps()`。
      * `V_lower`: 行列 `V` の下限、デフォルトは `eps()`。

!!! tip
    `fit!` または `compress` を呼び出す際にドメインエラーが発生した場合は、`options = NegativeDomain()` を使用してみてください。


# 戻り値

  * `epca`: `EPCA` サブタイプのインスタンス。
