```
qkf_negloglik(params::Vector{T}, data::QKData, N::Int, M::Int) where T<:Real -> Real
```

パラメータとデータに基づいて二次カルマンフィルタモデルの負の対数尤度を計算します。

# 引数

  * `params::Vector{T}`: QKModelに変換されるモデルパラメータのベクトル
  * `data::QKData`: 観測値とオプションの初期条件を持つデータコンテナ
  * `N::Int`: 状態ベクトルの次元
  * `M::Int`: 測定ベクトルの次元

# 戻り値

次の手順で計算された負の対数尤度値:

1. パラメータをQKModelに変換する
2. カルマンフィルタを実行する
3. 各期間の対数尤度の負の合計を取る

# 注意

この関数は通常、負の対数尤度を最小化することを目的とした最大尤度推定の目的関数として使用されます。

最適化のために、この関数をN、M、および指定されたデータでラップすることをお勧めします:

```julia
negloglik(params) = qkf_negloglik(params, data, N, M)
```
