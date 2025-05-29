```
MorgensternCopula{P}
```

フィールド:

```
- θ::Real - パラメータ
```

コンストラクタ

```
MorgensternCopula(θ)
```

二変量モルゲンシュテルンコピュラまたはFGMコピュラは、$\theta \in [-1,1]$でパラメータ化されています。次のように構成されます:

$$
C(u_1, u_2) = u_1u_2(1+\theta(1-u_1)(1-u_2))
$$

いくつかの特別なケースがあります:

  * θ = 0 のとき、これは独立コピュラです。

参考文献:

  * [Joe1997](@cite) Joe, Harry, Multivariate Models and Multivariate Dependence Concepts, Chapman & Hall. 1997.
