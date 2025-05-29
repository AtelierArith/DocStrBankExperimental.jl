```
kmeanspp_initialization(data::Vector{Float64}, k_means::Int)
```

ベクトルデータに対するクラスタ中心のK-means++初期化を実行します。

# 引数

  * `data::Vector{Float64}`: 入力データベクトル。
  * `k_means::Int`: クラスタの数。

# 戻り値

  * K-meansクラスタリングの初期中心の行列。
