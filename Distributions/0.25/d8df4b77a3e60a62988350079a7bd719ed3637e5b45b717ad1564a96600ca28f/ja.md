```
Gamma(α,θ)
```

*ガンマ分布*は、形状パラメータ`α`とスケール`θ`を持ち、確率密度関数は次のようになります。

$$
f(x; \alpha, \theta) = \frac{x^{\alpha-1} e^{-x/\theta}}{\Gamma(\alpha) \theta^\alpha},
\quad x > 0
$$

```julia
Gamma()          # 形状が単位、スケールが単位のガンマ分布、すなわちGamma(1, 1)
Gamma(α)         # 形状がα、スケールが単位のガンマ分布、すなわちGamma(α, 1)
Gamma(α, θ)      # 形状がα、スケールがθのガンマ分布

params(d)        # パラメータを取得、すなわち(α, θ)
shape(d)         # 形状パラメータを取得、すなわちα
scale(d)         # スケールパラメータを取得、すなわちθ
```

外部リンク

  * [ガンマ分布 - Wikipedia](http://en.wikipedia.org/wiki/Gamma_distribution)
