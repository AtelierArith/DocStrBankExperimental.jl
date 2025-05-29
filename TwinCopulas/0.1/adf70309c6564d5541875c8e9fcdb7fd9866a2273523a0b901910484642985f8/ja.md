```
GumbelCopula{P}
```

フィールド:

  * θ::Real - パラメータ

コンストラクタ

```
GumbelCopula(d,θ)
```

二変量 [Gumbel](https://en.wikipedia.org/wiki/Copula_(probability_theory)#Most_important_Archimedean_copulas) コピュラは $\theta \in [1,\infty)$ でパラメータ化されています。これは生成器を持つアーキメデスコピュラです:

$$
\phi(t) = \exp{-t^{\frac{1}{θ}}}
$$

いくつかの特別なケースがあります:

  * θ = 1 のとき、これは IndependentCopula です
  * θ = ∞ のとき、これは MCopula (上フレシェ-ヘフディング境界) です

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
