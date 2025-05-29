```
HMCDA(
    n_adapts::Int, δ::Float64, λ::Float64; ϵ::Float64 = 0.0;
    adtype::ADTypes.AbstractADType = AutoForwardDiff(),
)
```

ハミルトンモンテカルロサンプラー（Dual Averagingアルゴリズム）。

# 使用法

```julia
HMCDA(200, 0.65, 0.3)
```

# 引数

  * `n_adapts`: 適応に使用するサンプルの数。
  * `δ`: 目標受け入れ率。65%がよく推奨されます。
  * `λ`: 目標リープフロッグ長。
  * `ϵ`: 初期ステップサイズ; 0はTuringによって自動的に検索されることを意味します。
  * `adtype`: 自動微分（AD）バックエンド。指定されていない場合は、`ForwardDiff`が使用され、その`chunksize`は自動的に決定されます。

# 参考文献

詳細については、以下の論文を参照してください（[arXivリンク](https://arxiv.org/abs/1111.4246)）:

Hoffman, Matthew D., and Andrew Gelman. "The No-U-turn sampler: adaptively setting path lengths in Hamiltonian Monte Carlo." Journal of Machine Learning Research 15, no. 1 (2014): 1593-1623.
