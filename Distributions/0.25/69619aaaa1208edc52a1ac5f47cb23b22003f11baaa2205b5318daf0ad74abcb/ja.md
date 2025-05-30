```
LogitNormal(μ,σ)
```

*ロジット正規分布*は、ロジットが[`Normal`](@ref)分布に従う確率変数の分布です。逆に、正規分布に従う確率変数にロジスティック関数を適用すると、得られた確率変数はロジット正規分布に従います。

もし$X \sim \operatorname{Normal}(\mu, \sigma)$であれば、$\operatorname{logistic}(X) \sim \operatorname{LogitNormal}(\mu,\sigma)$です。

確率密度関数は次のようになります。

$$
f(x; \mu, \sigma) = \frac{1}{x \sqrt{2 \pi \sigma^2}}
\exp \left( - \frac{(\text{logit}(x) - \mu)^2}{2 \sigma^2} \right),
\quad x > 0
$$

ここで、ロジット関数は次のようになります。

$$
\text{logit}(x) = \ln\left(\frac{x}{1-x}\right)
\quad 0 < x < 1
$$

```julia
LogitNormal()        # ロジット正規分布、ロジット平均がゼロ、スケールが単位
LogitNormal(μ)       # ロジット正規分布、ロジット平均 μ、スケールが単位
LogitNormal(μ, σ)    # ロジット正規分布、ロジット平均 μ、スケール σ

params(d)            # パラメータを取得、すなわち (μ, σ)
median(d)            # 中央値を取得、すなわち logistic(μ)
```

以下の特性には解析的解がありませんが、数値的近似があります。数値最適化のためのパッケージ依存を避けるため、現在は実装されていません。

```julia
mean(d)
var(d)
std(d)
mode(d)
```

同様に、歪度、尖度、エントロピーも実装されていません。

外部リンク

  * [ロジット正規分布 - Wikipedia](https://en.wikipedia.org/wiki/Logit-normal_distribution)
