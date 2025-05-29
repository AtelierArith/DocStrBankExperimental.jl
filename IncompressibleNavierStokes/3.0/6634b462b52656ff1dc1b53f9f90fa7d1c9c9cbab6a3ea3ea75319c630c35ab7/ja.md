```julia
Qfield(u, setup) -> Any

```

$$
Q
$$

-フィールド [Jeong1995](@cite) を次のように計算します。

$$
Q = - \frac{1}{2} \sum_{α, β} \frac{\partial u^α}{\partial x^β}
\frac{\partial u^β}{\partial x^α}.
$$

微分可能なバージョン。
