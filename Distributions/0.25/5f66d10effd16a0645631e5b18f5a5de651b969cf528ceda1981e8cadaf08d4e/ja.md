```
InverseGaussian(μ,λ)
```

*逆ガウス分布*は、平均 `μ` と形状 `λ` を持ち、確率密度関数は次のようになります。

$$
f(x; \mu, \lambda) = \sqrt{\frac{\lambda}{2\pi x^3}}
\exp\!\left(\frac{-\lambda(x-\mu)^2}{2\mu^2x}\right), \quad x > 0
$$

```julia
InverseGaussian()              # 平均1、形状1の逆ガウス分布、すなわち InverseGaussian(1, 1)
InverseGaussian(μ),            # 平均μ、形状1の逆ガウス分布、すなわち InverseGaussian(μ, 1)
InverseGaussian(μ, λ)          # 平均μ、形状λの逆ガウス分布

params(d)           # パラメータを取得、すなわち (μ, λ)
mean(d)             # 平均パラメータを取得、すなわち μ
shape(d)            # 形状パラメータを取得、すなわち λ
```

外部リンク

  * [逆ガウス分布 - Wikipedia](http://en.wikipedia.org/wiki/Inverse_Gaussian_distribution)
