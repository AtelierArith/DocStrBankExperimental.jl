```
Pareto(α,θ)
```

*パレート分布*は、形状 `α` とスケール `θ` を持ち、確率密度関数は次のようになります。

$$
f(x; \alpha, \theta) = \frac{\alpha \theta^\alpha}{x^{\alpha + 1}}, \quad x \ge \theta
$$

```julia
Pareto()            # 単位形状と単位スケールのパレート分布、すなわち Pareto(1, 1)
Pareto(α)           # 形状 α と単位スケールのパレート分布、すなわち Pareto(α, 1)
Pareto(α, θ)        # 形状 α とスケール θ のパレート分布

params(d)        # パラメータを取得、すなわち (α, θ)
shape(d)         # 形状パラメータを取得、すなわち α
scale(d)         # スケールパラメータを取得、すなわち θ
```

外部リンク

  * [パレート分布 - Wikipedia](http://en.wikipedia.org/wiki/Pareto_distribution)
