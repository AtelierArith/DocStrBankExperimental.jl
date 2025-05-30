```
PGeneralizedGaussian(μ, α, p)
```

*p-一般化ガウス分布*は、より一般的には指数冪または一般化正規分布として知られ、スケール `α`、位置 `μ`、形状 `p` を持ち、確率密度関数は次のようになります。

$$
f(x, \mu, \alpha, p) = \frac{p}{2\alpha\Gamma(1/p)} e^{-(\frac{|x-\mu|}{\alpha})^p} \quad x \in (-\infty, +\infty) , \alpha > 0, p > 0
$$

p-一般化ガウス分布（GGD）は、正規分布（`p = 2`）およびラプラス分布（`p = 1`）を特別なケースとして組み込んだパラメトリック分布です。`p → ∞` のとき、分布は `[μ - α, μ + α]` 上の一様分布に近づきます。

```julia
PGeneralizedGaussian()           # 位置0、スケール√2、形状2のGGD（正規分布）
PGeneralizedGaussian(μ, α, p)    # 位置μ、スケールα、形状pのGGD

params(d)                        # パラメータを取得、すなわち (μ, α, p)
location(d)                      # 位置パラメータμを取得
scale(d)                         # スケールパラメータαを取得
shape(d)                         # 形状パラメータpを取得
```

外部リンク

  * [ウィキペディアの一般化ガウス分布](http://en.wikipedia.org/wiki/Generalized_normal_distribution)
  * [参照実装](https://www.researchgate.net/publication/254282790_Simulation_of_the_p-generalized_Gaussian_distribution)

```
