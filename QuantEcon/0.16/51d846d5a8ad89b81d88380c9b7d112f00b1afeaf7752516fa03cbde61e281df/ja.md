```
qnwdist(
    d::Distributions.ContinuousUnivariateDistribution, N::Int,
    q0::Real=0.001, qN::Real=0.999, method::Union{T,Type{T}}=Quantile
) where T
```

分布 `d` のために、量子 `q0` から量子 `qN` までの `N` 個の数値重みとノードを構築します。`method` は次のいずれかにすることができます：

  * `Even`: ノードは量子の間で均等に配置されます
  * `Quantile`: ノードは均等に配置された量子値に置かれます

重みを構築するために、ノードを各ノードの中心にあるセルに分割することを考えます。具体的には、記法 `z_i` は `i` 番目のノードを意味し、`z_{i-1/2}` はノード `z_{i-1}` と `z_i` の間の 1/2 を表します。次に、重みは次のように決定されます：

  * `weights[1] = cdf(d, z_{1+1/2})`
  * `weights[N] = 1 - cdf(d, z_{N-1/2})`
  * `weights[i] = cdf(d, z_{i+1/2}) - cdf(d, z_{i-1/2})` ただし、すべての i は 2:N-1 の範囲です

実際、この戦略はノード `i` に、ノード `i` のセル内で発生する確率変数に関連するすべての確率を割り当てます。

重みは常に 1 に合計されるため、適切な確率分布として使用できます。これは、`E[f(x) | x ~ d] ≈ dot(f.(nodes), weights)` を意味します。
