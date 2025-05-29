```
MardiaCopula{P}
```

フィールド:

```
- θ::Real - パラメータ
```

コンストラクタ

```
MardiaCopula(θ)
```

二変量マルディアコピュラは、$\theta \in [-1,1]$でパラメータ化されています。次のように構成されます:

$$
C(u_1, u_2) = \frac{\theta^2(1+\theta)}{2}\min\{u_1,u_2\} + (1-\theta^2)u_1u_2 + \frac{\theta^2(1-\theta)}{2}\max\{u_1+u_2-1,0\}
$$

いくつかの特別なケースがあります:

  * θ = 0 のとき、独立コピュラです
  * θ = 1 のとき、MCopula（上フレシェ・ホエフディング境界）です
  * θ = -1 のとき、WCopula（下フレシェ・ホエフディング境界）です

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
