```
StopWhenFirstOrderProgress <: StoppingCriterion
```

Riemannian適応正則化によるキュービック（ARC）ソルバーに関連する停止基準で、現在の（外部）反復におけるモデル関数が、

$$
    m(X) = f(p) + <X, \operatorname{grad}f(p)>
      + \frac{1}{2} <X, \operatorname{Hess} f(p)[X]> +  \frac{σ}{3} \lVert X \rVert^3,
$$

接空間$T_{p}\mathcal M$上で、現在の反復$X_k$において次の条件を満たすことを示します。

$$
m(X_k) \leq m(0)
\quad\text{ および }\quad
\lVert \operatorname{grad} m(X_k) \rVert ≤ θ \lVert X_k \rVert^2
$$

# フィールド

  * `θ`:      第二条件における因子$θ$
  * `at_iteration`: 停止基準が満たされた反復（`i=0`を含む）を示し、満たされていない間は`-1`です。
