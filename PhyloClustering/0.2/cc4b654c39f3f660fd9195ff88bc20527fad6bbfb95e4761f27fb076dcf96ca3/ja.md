```
kmeans_label(tree::AbstractMatrix{<:Real}, n::Int64; init::String="k-means++", rng::AbstractRNG=Random.GLOBAL_RNG)
```

系統樹のグループに対するYinyang K-meansクラスタリングから予測ラベルを取得します。

# 引数

  * `tree`: B * Nのツリーマトリックス（ツリーマトリックスの各列は二分割形式のB次元ツリーです）。
  * `n`: クラスターの数。
  * `init`（デフォルトは`k-means++`）: 初期化に使用されるアルゴリズムの1つです。代わりに、`rand`を使用して初期化のためのランダムな点を選択することもできます。
  * `rng`: RNGオブジェクト。

# 出力

各ツリーに対する予測ラベルを含む長さNの`Vector`オブジェクト（それが属するクラスター）。
