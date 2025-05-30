```
DirichletMultinomial
```

[ディリクレ-多項分布](https://en.wikipedia.org/wiki/Dirichlet-multinomial_distribution)は、各サンプルが共通のディリクレ分布から引かれたわずかに異なる確率ベクトルを持つ多項分布からの引き出しの分布です。

これは、すべての観測が単一の固定された確率ベクトルから生じると仮定する多項分布とは対照的です。これにより、ディリクレ-多項分布は多項分布よりも変動の大きい（すなわち、過分散した）カウントデータを扱うことができます。

確率質量関数は次のように与えられます。

$$
f(x; \alpha) = \frac{n! \Gamma(\alpha_0)}
{\Gamma(n+\alpha_0)}\prod_{k=1}^K\frac{\Gamma(x_{k}+\alpha_{k})}
{x_{k}! \Gamma(\alpha_{k})}
$$

ここで

  * $$
    n = \sum_k x_k
    $$
  * $$
    \alpha_0 = \sum_k \alpha_k
    $$

```julia
# αをベクトルとする
DirichletMultinomial(n, α) # パラメータベクトルαを持つn回の試行のためのディリクレ-多項分布。

# kを正の整数とする
DirichletMultinomial(n, k) # n回の試行と長さkの1のベクトルを持つパラメータのディリクレ-多項分布。
```
