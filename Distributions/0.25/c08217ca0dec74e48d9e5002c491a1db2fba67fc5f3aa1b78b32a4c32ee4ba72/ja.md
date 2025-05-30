```
BetaBinomial(n,α,β)
```

*ベータ二項分布*は、成功の確率 `p` が[`ベータ`](@ref)に従って分布する[`二項`](@ref)分布の複合分布です。3つのパラメータを持ちます：`n`、試行の回数、そして2つの形状パラメータ `α`、`β`。

$$
P(X = k) = {n \choose k} B(k + \alpha, n - k + \beta) / B(\alpha, \beta),  \quad \text{ for } k = 0,1,2, \ldots, n.
$$

```julia
BetaBinomial(n, α, β)      # n回の試行と形状パラメータα、βを持つベータ二項分布

params(d)       # パラメータを取得します。すなわち (n, α, β)
ntrials(d)      # 試行の回数を取得します。すなわち n
```

外部リンク：

  * [ベータ二項分布 - Wikipedia](https://en.wikipedia.org/wiki/Beta-binomial_distribution)
