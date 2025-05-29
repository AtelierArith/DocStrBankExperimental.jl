```
ディリクレ
```

[ディリクレ分布](http://en.wikipedia.org/wiki/Dirichlet_distribution)は、カテゴリカル分布または多項分布の共役事前分布としてよく使用されます。パラメータ $\alpha = (\alpha_1, \ldots, \alpha_k)$ を持つディリクレ分布の確率密度関数は次のようになります：

$$
f(x; \alpha) = \frac{1}{B(\alpha)} \prod_{i=1}^k x_i^{\alpha_i - 1}, \quad \text{ ただし }
B(\alpha) = \frac{\prod_{i=1}^k \Gamma(\alpha_i)}{\Gamma \left( \sum_{i=1}^k \alpha_i \right)},
\quad x_1 + \cdots + x_k = 1
$$

```julia
# alphaをベクトルとする
Dirichlet(alpha)         # パラメータベクトルalphaを持つディリクレ分布

# aを正のスカラーとする
Dirichlet(k, a)          # パラメータa * ones(k)を持つディリクレ分布
```
