```
StopWhenFirstOrderProgress <: StoppingCriterion
```

Riemannian適応正則化による立方体（ARC）ソルバーに関連する停止基準であり、現在の（外部）反復におけるモデル関数は、

$$
m_k(X) = f(p_k) + ⟨X, \operatorname{grad} f(p^{(k)})⟩ + \frac{1}{2}⟨X, \operatorname{Hess} f(p^{(k)})[X]⟩ + \frac{σ_k}{3}\lVert X \rVert^3
$$

接空間$T_{p}\mathcal M$上で、現在の反復$X_k$において次の条件を満たすことを示します。

$$
m(X_k) \leq m(0)
\quad\text{ および }\quad
\lVert \operatorname{grad} m(X_k) \rVert ≤ θ \lVert X_k \rVert^2
$$

# フィールド

  * `θ`:      第二条件における因子$θ$
  * `at_iteration::Int`: 停止基準が最後に停止を示した反復を示す整数で、ソルバーが開始する前（`0`）である可能性もあります。負の値は、まだその場合ではないことを示します;

# コンストラクタ

```
StopWhenAllLanczosVectorsUsed(θ)
```
