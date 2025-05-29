```
B11Copula{P}
```

フィールド:

```
- θ::Real - パラメータ
```

コンストラクタ

```
B11Copula(θ)
```

二変量B11コピュラは、$\theta \in [0,1]$でパラメータ化されています。次のように構築されます:

$$
C(u_1, u_2) = \theta \min\{u_1,u_2\} + (1-\theta)u_1u_2
$$

いくつかの特別なケースがあります:

  * θ = 0 のとき、これはIndependentCopulaです
  * θ = 1 のとき、これはMCopula（上フレシェ・ホフディング境界）です

参考文献:

  * [Joe1997](@cite) Joe, Harry, Multivariate Models and Multivariate Dependence Concepts, Chapman & Hall. 1997.
