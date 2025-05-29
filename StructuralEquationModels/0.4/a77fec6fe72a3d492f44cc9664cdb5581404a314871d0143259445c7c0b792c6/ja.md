加重最小二乗推定。現在のところ、`RAMSymbolic` 暗示型でのみ利用可能です。

# コンストラクタ

```
SemWLS(;
    observed,
    meanstructure = false,
    wls_weight_matrix = nothing,
    wls_weight_matrix_mean = nothing,
    approximate_hessian = false,
    kwargs...)
```

# 引数

  * `observed`: モデルの `SemObserved` 部分
  * `meanstructure::Bool`: モデルに平均構造はありますか？
  * `approximate_hessian::Bool`: ヘッセ行列を近似に置き換えますか？
  * `wls_weight_matrix`: 加重最小二乗のための重み行列。GLS推定（$0.5*(D^T*kron(S,S)*D)$、ここで D は重複行列、S は観測共分散行列の逆行列）にデフォルト設定されています。
  * `wls_weight_matrix_mean`: 加重最小二乗の平均部分のための重み行列。観測共分散行列の逆行列にデフォルト設定されています（GLS推定）。

# 例

```julia
my_wls = SemWLS(observed = my_observed)
```

# インターフェース

解析的勾配が利用可能で、平均構造のないモデルに対しても解析的ヘッセ行列が利用可能です。
