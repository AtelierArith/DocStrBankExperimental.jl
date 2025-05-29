```
Weibull(α,θ)
```

*ウィーバル分布*は、形状 `α` とスケール `θ` を持ち、確率密度関数は次のようになります。

$$
f(x; \alpha, \theta) = \frac{\alpha}{\theta} \left( \frac{x}{\theta} \right)^{\alpha-1} e^{-(x/\theta)^\alpha},
    \quad x \ge 0
$$

```julia
Weibull()        # 単位形状と単位スケールのウィーバル分布、すなわち Weibull(1, 1)
Weibull(α)       # 形状 α と単位スケールのウィーバル分布、すなわち Weibull(α, 1)
Weibull(α, θ)    # 形状 α とスケール θ のウィーバル分布

params(d)        # パラメータを取得、すなわち (α, θ)
shape(d)         # 形状パラメータを取得、すなわち α
scale(d)         # スケールパラメータを取得、すなわち θ
```

外部リンク

  * [ウィーバル分布 - Wikipedia](http://en.wikipedia.org/wiki/Weibull_distribution)
