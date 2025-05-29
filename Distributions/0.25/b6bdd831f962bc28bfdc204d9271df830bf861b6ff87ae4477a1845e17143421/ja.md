```
フレーシェ(α,θ)
```

*フレーシェ分布*は、形状 `α` とスケール `θ` を持ち、確率密度関数は次のようになります。

$$
f(x; \alpha, \theta) = \frac{\alpha}{\theta} \left( \frac{x}{\theta} \right)^{-\alpha-1}
e^{-(x/\theta)^{-\alpha}}, \quad x > 0
$$

```julia
Frechet()        # 単位形状と単位スケールのフレーシェ分布、すなわち Frechet(1, 1)
Frechet(α)       # 形状 α と単位スケールのフレーシェ分布、すなわち Frechet(α, 1)
Frechet(α, θ)    # 形状 α とスケール θ のフレーシェ分布

params(d)        # パラメータを取得、すなわち (α, θ)
shape(d)         # 形状パラメータを取得、すなわち α
scale(d)         # スケールパラメータを取得、すなわち θ
```

外部リンク

  * [Fréchet_distribution on Wikipedia](http://en.wikipedia.org/wiki/Fréchet_distribution)
