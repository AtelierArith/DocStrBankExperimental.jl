```
BetaPrime(α, β)
```

*ベータプライム分布*の確率密度関数は

$$
f(x; \alpha, \beta) = \frac{1}{B(\alpha, \beta)}
x^{\alpha - 1} (1 + x)^{- (\alpha + \beta)}, \quad x > 0
$$

ベータプライム分布は、$X \sim \operatorname{Beta}(\alpha, \beta)$ のときに $\frac{X}{1 - X} \sim \operatorname{BetaPrime}(\alpha, \beta)$ という関係を通じて [`Beta`](@ref) 分布に関連しています。

```julia
BetaPrime()        # BetaPrime(1, 1) と同等
BetaPrime(α)       # BetaPrime(α, α) と同等
BetaPrime(α, β)    # 形状パラメータ α と β を持つベータプライム分布

params(d)          # パラメータを取得、すなわち (α, β)
```

外部リンク

  * [ベータプライム分布 - Wikipedia](http://en.wikipedia.org/wiki/Beta_prime_distribution)
