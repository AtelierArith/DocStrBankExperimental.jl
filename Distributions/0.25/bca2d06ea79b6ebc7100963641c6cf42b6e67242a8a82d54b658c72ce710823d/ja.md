```
Soliton(K::Integer, M::Integer, δ::Real, atol::Real=0) <: Distribution{Univariate, Discrete}
```

ロバストソリトン分布の長さ `K`、モード `M`（すなわち、ロバストコンポーネントスパイクの位置）、剥離プロセスの失敗確率 `δ`、および最小非ゼロ確率質量 `atol`。より具体的には、`pdf(Ω, i)<atol` となる次数 `i` は `0` に設定されます。`atol=0` とすると、通常のロバストソリトン分布が得られます。

```julia
Soliton(K, M, δ)        # ロバストソリトン分布（atol=0）
Soliton(K, M, δ, atol)  # 最小非ゼロ確率質量 atol を持つロバストソリトン分布

params(Ω)               # パラメータを取得、すなわち (K, M, δ, atol)
degrees(Ω)              # 非ゼロ確率質量を持つ次数から構成されたベクトルを返す
pdf(Ω, i)               # i で pdf を評価
cdf(Ω, i)               # i で cdf を評価
rand(Ω)                 # Ω からサンプリング
rand(Ω, n)              # Ω から n サンプルを引く
```

外部リンク：

  * [ソリトン分布 - Wikipedia](https://en.wikipedia.org/wiki/Soliton_distribution)
