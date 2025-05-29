```
Exponential(θ)
```

*スケールパラメータ* `θ` を持つ *指数分布* の確率密度関数は

$$
f(x; \theta) = \frac{1}{\theta} e^{-\frac{x}{\theta}}, \quad x > 0
$$

```julia
Exponential()      # スケールが1の指数分布、すなわち Exponential(1)
Exponential(θ)     # スケールがθの指数分布

params(d)          # パラメータを取得、すなわち (θ,)
scale(d)           # スケールパラメータを取得、すなわち θ
rate(d)            # レートパラメータを取得、すなわち 1 / θ
```

外部リンク

  * [指数分布 - Wikipedia](http://en.wikipedia.org/wiki/Exponential_distribution)
