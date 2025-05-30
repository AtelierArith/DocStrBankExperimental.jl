```
LogNormal(μ,σ)
```

*対数正規分布*は、[`Normal`](@ref)変数の指数の分布です：$X \sim \operatorname{Normal}(\mu, \sigma)$ の場合、$\exp(X) \sim \operatorname{LogNormal}(\mu,\sigma)$ です。確率密度関数は次のようになります。

$$
f(x; \mu, \sigma) = \frac{1}{x \sqrt{2 \pi \sigma^2}}
\exp \left( - \frac{(\log(x) - \mu)^2}{2 \sigma^2} \right),
\quad x > 0
$$

```julia
LogNormal()          # 対数正規分布（対数平均がゼロ、スケールが単位）
LogNormal(μ)         # 対数正規分布（対数平均がμ、スケールが単位）
LogNormal(μ, σ)      # 対数正規分布（対数平均がμ、スケールがσ）

params(d)            # パラメータを取得（μ, σ）
meanlogx(d)          # log(X)の平均を取得（μ）
varlogx(d)           # log(X)の分散を取得（σ^2）
stdlogx(d)           # log(X)の標準偏差を取得（σ）
```

外部リンク

  * [Wikipediaの対数正規分布](http://en.wikipedia.org/wiki/Log-normal_distribution)
