```
GumbelBarnettCopula{P}
```

フィールド:

  * θ::Real - パラメータ

コンストラクタ

```
GumbelBarnettCopula(θ)
```

二変量Gumbel-Barnettコピュラは、$\theta \in (0,1]$でパラメータ化されています。これは、生成器を持つアーキメデアンコピュラです：

$$
\phi(t) = \exp{θ^{-1}(1-e^{t})}, 0 \leq \theta \leq 1.
$$

いくつかの特別なケースがあります：

  * θ = 0 のとき、これはIndependentCopulaです。

参考文献:

  * [joe2014](@cite) Joe, H. (2014). Dependence modeling with copulas. CRC press, Page.437
  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
