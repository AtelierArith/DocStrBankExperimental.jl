```
dualgraph(dist::Matrix{Float64}; method::Symbol = :inverse, σ::Float64 = 1.0)
```

与えられた非自明な固有ベクトルメトリックに基づいて双対グラフの重み行列を構築します。

# 入力引数

  * `dist::Matrix{Float64}`: 固有ベクトル距離行列
  * `method::Symbol`: デフォルトは固有ベクトル間の距離の逆数を取ることです。双対グラフのエッジ重みを構築する方法。オプション: `:inverse`, `:gaussian`。
  * `σ::Float64`: デフォルトは `1.0`。ガウス分散パラメータ。

# 出力引数

  * `G_star::GraphSig`: 双対グラフの重み行列を含む `GraphSig` オブジェクト。
