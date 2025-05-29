```
kmeanspp_initialization(data::Matrix{<:Real}, k_means::Int)
```

クラスタ中心のためのK-means++初期化を実行します。

# 引数

  * `data::Matrix{<:Real}`: 各行がデータポイントである入力データ行列。
  * `k_means::Int`: クラスターの数。

# 戻り値

  * K-meansクラスタリングの初期中心の行列。
