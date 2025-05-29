```
RafteryCopula{P}
```

フィールド:

```
- θ::Real - パラメータ
```

コンストラクタ

```
RafteryCopula(θ)
```

二変量Rafteryコピュラは、$\theta \in [0,1]$でパラメータ化されています。次のように構成されます:

$$
C(u_1, u_2) = \min\{u_1,u_2\} +\frac{1-\theta}{1+\theta}(u_1u_2)^{1/(1-\theta)}\left \{1-(\max\{u_1,u_2\})^{-(1+\theta)/(1-\theta)}  \right \}
$$

いくつかの特別なケースがあります:

  * θ = 0 のとき、独立コピュラです
  * θ = 1 のとき、MCopula（上フレシェ-ホエフディング境界）です

参考文献:

  * [Joe1997](@cite) Joe, Harry, Multivariate Models and Multivariate Dependence Concepts, Chapman & Hall. 1997.
