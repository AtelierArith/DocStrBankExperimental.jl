```
FrechetCopula{P}
```

フィールド:

```
- θ1::Real - パラメータ
- θ2::Real - パラメータ
```

コンストラクタ

```
FrechetCopula(θ1, θ2)
```

二変量フレーシェコピュラは、$\theta_{i} \in [0,1], i = 1,2$ によってパラメータ化され、$\theta_1 + \theta_2 \leq 1$ です。次のように構成されます:

$$
C(u_1, u_2) = \theta_1 \min\{u_1, u_2\} + (1- \theta_1 - \theta_2)u_1u_2 + \theta_2 \max\{u_1 + u_2 - 1, 0\}
$$

いくつかの特別なケースがあります:

  * θ1 = θ2 = 0 のとき、これは独立コピュラです
  * θ1 = 1 のとき、これはMCopula（上フレーシェ-ホエフディング境界）です
  * θ2 = 1 のとき、これはWCopula（下フレーシェ-ホエフディング境界）です

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
