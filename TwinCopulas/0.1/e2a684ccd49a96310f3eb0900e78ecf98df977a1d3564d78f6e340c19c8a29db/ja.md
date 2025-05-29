```
ClaytonCopula{P}
```

フィールド:

  * θ::Real - パラメータ

コンストラクタ

```
ClaytonCopula(d,θ)
```

二変量 [Clayton](https://en.wikipedia.org/wiki/Copula_(probability_theory)#Most_important_Archimedean_copulas) コピュラは $\theta \in [-1,\infty)$ でパラメータ化されています。これは生成器を持つアーキメデスコピュラです:

$$
\phi(t) = \left(1+\mathrm{sign}(\theta)*t\right)^{-1\frac{1}{\theta}}
$$

いくつかの特別なケースがあります:

  * θ = -1 のとき、これは WCopula (下フレシェ-ホエフディング境界) です
  * θ = 0 のとき、これは IndependentCopula です
  * θ = 1 のとき、これは UtilCopula です
  * θ = ∞ のとき、これは MCopula (上フレシェ-ホエフディング境界) です

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
