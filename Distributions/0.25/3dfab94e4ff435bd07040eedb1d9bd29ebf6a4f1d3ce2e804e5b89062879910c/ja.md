```
Beta(α, β)
```

*ベータ分布*の確率密度関数は

$$
f(x; \alpha, \beta) = \frac{1}{B(\alpha, \beta)}
 x^{\alpha - 1} (1 - x)^{\beta - 1}, \quad x \in [0, 1]
$$

ベータ分布は、$X \sim \operatorname{Gamma}(\alpha)$ および $Y \sim \operatorname{Gamma}(\beta)$ が独立であるとき、$X / (X + Y) \sim \operatorname{Beta}(\alpha, \beta)$ という性質を通じて [`Gamma`](@ref) 分布に関連しています。

```julia
Beta()        # Beta(1, 1) と同等
Beta(α)       # Beta(α, α) と同等
Beta(α, β)    # 形状パラメータ α と β を持つベータ分布

params(d)     # パラメータを取得、すなわち (α, β)
```

外部リンク

  * [ベータ分布 - Wikipedia](http://en.wikipedia.org/wiki/Beta_distribution)
