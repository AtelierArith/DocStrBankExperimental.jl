```
InvGaussianCopula{P}
```

フィールド:

  * θ::Real - パラメータ

コンストラクタ

```
InvGaussianCopula(θ)
```

二変量逆ガウスコピュラは、$\theta \in [0,\infty)$ でパラメータ化されています。これは、生成器を持つアルキメデスコピュラです：

$$
\phi(t) = \exp{\frac{1-\sqrt{1+2θ^{2}t}}{θ}}.
$$

逆ガウスアルキメデスコピュラに関する詳細は、以下にあります：

```
Mai, Jan-Frederik, and Matthias Scherer. Simulating copulas: stochastic models, sampling algorithms, and applications. Vol. 6. # N/A, 2017. Page 74.
```

いくつかの特別なケースがあります：

  * θ = 0 のとき、これは IndependentCopula です。

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
